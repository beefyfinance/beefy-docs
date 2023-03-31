---
description: Tradução feita a partir da atualização de fevereiro de 2023
---

# Contrato BeefyWrapper

O [contrato BeefyWrapper](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyWrapper.sol) é uma interface adaptadora ERC-4626 que torna um [contrato-de-cofre.md](../contrato-de-cofre.md "mention") da Beefy compatível com o [padrão](https://eips.ethereum.org/EIPS/eip-4626) ERC-4626. Ele desbloqueia a capacidade de composição do padrão e permite uma interface e interação mais suave com os cofres da Beefy por protocolos externos, sem a necessidade de adaptadores e plug-ins adicionais.

Esta página apresenta alguns dos antecedentes do padrão ERC-4626 e a funcionalidade do contrato BeefyWrapper.

## Por que ERC-4626?

O objetivo da norma ERC-4626 é resolver os problemas causados pela diversidade de projetos de cofres encontrados em toda a DeFi. Muitos protocolos incorporaram conceitos de cofre em sua arquitetura, reinventando a roda para adequá-la a sua própria arquitetura e casos de uso únicos. Isto significa que projetos externos esperando implementar uma gama de diferentes cofres precisam adaptar e integrar seu código para reconciliá-lo com as peculiaridades do design único de cada protocolo de cofres.

O novo padrão reconhece algumas funções comuns na maioria dos cofres e sugere que a harmonização desta funcionalidade em um único padrão pode ajudar a mitigar a quantidade de adaptações e plug-ins necessários para trabalhar com a maioria dos cofres. Para protocolos como a Beefy, a adoção do ERC-4626 para nossos cofres da Beefy ajuda a facilitar o desenvolvimento de novos produtos com base em nossos produtos e, como resultado, promete aumentar a gama de casos de uso disponíveis para nossos usuários.

## Funções do Contrato

A funcionalidade do contrato BeefyWrapper facilita a cunhagem e queima das tokens embrulhadas de cofre da Beefy em troca da transferência das tokens de cofre da Beefy do chamador. Ele também substitui as funções padrão de depósito e retirada para facilitar o depósito no cofre principal da Beefy, em troca da cunhagem e queima das tokens embrulhadas do cofre da Beefy.

### wrap()

Transfere a quantidade especificada de tokens do cofre da Beefy Vault do chamador para o contrato embalador para cunhar a mesma quantidade de tokens embaladas do cofre da Beefy para o chamador.

```solidity
// Wraps an amount of vault share tokens.
/// "amount" parameter is the total amount of vault share tokens to be wrapped.

function wrap(uint256 amount) public {

    // Transfers the specified amount of the caller's Beefy Vault tokens to the wrapper.
    IERC20Upgradeable(vault).safeTransferFrom(msg.sender, address(this), amount);
    
    // Mints the specified amount wrapped Beefy Vault tokens to the caller.
    _mint(msg.sender, amount);
}
```

### wrapAll()

Utiliza a função _wrap()_, mas utilizando o saldo total do chamador como o parâmetro "amount".

```solidity
// Wraps all vault share tokens owned by the caller.

function wrapAll() external {
    wrap(IERC20Upgradeable(vault).balanceOf(msg.sender));
}
```

### unwrap()

Queima a quantidade especificada dos tokens embrulhados de cofre da Beefy do chamador, para transferir a mesma quantidade de tokens não embrulhados do contrato embrulhador de volta para o chamador.

```solidity
// Unwraps an amount of vault share tokens.
/// "amount" parameter is the total amount of vault share tokens to be unwrapped.

function unwrap(uint256 amount) public {

    // Burns the specified amount of the caller's wrapped Beefy Vault tokens.
    _burn(msg.sender, amount);
    
    // Transfers the specified amount of Beefy Vault tokens back to the caller.
    IERC20Upgradeable(vault).safeTransfer(msg.sender, amount);
}
```

### unwrapAll()

Utiliza a função un_wrap()_, mas utilizando o saldo total do chamador como o parâmetro "amount".

```solidity
// Unwraps all wrapped tokens owned by the caller.

function unwrapAll() external {
    unwrap(balanceOf(msg.sender));
}
```

### \_deposit()

Substitui a função padrão \_deposit() para interagir com o contrato embrulhador e emitir tokens embrulhadas de cofre da Beefy no lugar da versão não embrulhada. Caso contrário, facilita uma transferência normal para o cofre da Beefy.

```solidity
// Deposit assets to the vault and mint an equal number of wrapped tokens to vault shares.
/// "caller" parameter is the address of the sender of the assets.
/// "receiver" parameter is the address of the receiver of the wrapped tokens.
/// "assets" parameter is the amount of assets being deposited.
/// "shares parameter is the amount of shares being minted.

function _deposit(address caller, address receiver, uint256 assets, uint256 shares) internal virtual override {

    // Transfers the caller's tokens to the wrapper.
    IERC20Upgradeable(asset()).safeTransferFrom(caller, address(this), assets);
    uint balance = IERC20Upgradeable(vault).balanceOf(address(this));
    
    // Deposits the caller's tokens into the Beefy Vault.
    IVault(vault).deposit(assets);

    // Mints wrapped tokens to the receiver.
    shares = IERC20Upgradeable(vault).balanceOf(address(this)) - balance;
    _mint(receiver, shares);

    // Emits the Deposit event to signify a successful deposit.
    emit Deposit(caller, receiver, assets, shares);
}
```

### \_withdraw()

Substitui a função \_withdraw() padrão para interagir com as tokens embrulhadas do cofre da Beefy no lugar da versão não encapsulada. Caso contrário, facilita uma retirada normal do cofre da  Beefy e retorna as tokens subjacentes ao destinatário.

```solidity
// Burn wrapped tokens and withdraw assets from the vault.
/// "caller" parameter is the address of the caller of the withdraw.
/// "receiver" parameter is the address of the receiver of the assets.
/// "owner" parameter is the address of the owner of the burnt shares.
/// "assets" parameter is the amount of assets being withdrawn.
/// "shares parameter is the amount of shares being burnt.

function _withdraw(address caller, address receiver, address owner, uint256 assets, uint256 shares) internal virtual override {
    
    // Checks caller is not the contract's owner, and that the caller's spend                 allowance is sufficient for the call.
    if (caller != owner) {
        _spendAllowance(owner, caller, shares);
    }
    
    // Burns the caller's wrapped tokens.
    _burn(owner, shares);

    // Withdraws the caller's assets from the Beefy Vault.
    IVault(vault).withdraw(shares);
    uint balance = IERC20Upgradeable(asset()).balanceOf(address(this));
    if (assets > balance) {
        assets = balance;
    }

    // Transfers the caller's assets back to the receiver.
    IERC20Upgradeable(asset()).safeTransfer(receiver, assets);
    
    // Emits the Withdraw event to signify a successful withdrawal.
    emit Withdraw(caller, receiver, owner, assets, shares);
}
```

### totalAssets()

Substitui a função totalAssets() padrão para buscar o total de ativos presentes no cofre.

```solidity
// Fetches and returns the total assets as a uint256 value.

function totalAssets() public view virtual override returns (uint256) {

    return IVault(vault).balance();

}
```

### totalSupply()

Substitui a função totalSupply() padrão para buscar o total de cotas emitidas pelo cofre.

```solidity
// Fetches and returns the total vault shares as a uint256 value.

function totalSupply() public view virtual override(ERC20Upgradeable, IERC20Upgradeable) returns (uint256) {

    return IERC20Upgradeable(vault).totalSupply();
    
}
```

## Contrato BeefyWrapperFactory

O contrato BeefyWrapperFactory é um contrato de fábrica que fornece um padrão de proxy mínimo para uso na criação de novos embrulhadores de cofres da Beefy. Um contrato de fábrica permite que os usuários gerem e implantem seus próprios contratos proxy que apontam para o mesmo contrato de implementação, onde reside a lógica.

Por meio do BeefyWrapperFactory, os contratos BeefyWrapper podem ser implantados para qualquer cofre. O contrato de fábrica tem apenas uma função chave - clone().

### clone()

Usa o modelo de proxy padrão OpenZeppelin [ClonesUpgradeable.sol](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/master/contracts/proxy/ClonesUpgradeable.sol) para criar um contrato de proxy que é um clone do contrato BeefyWrapper.

```solidity
// Creates a new Beefy Vault wrapper as a proxy of the template instance.
/// "_vault" parameter is the cloned Beefy Vault.
/// "proxy" return is the new proxied Beefy Vault wrapper.

function clone(address _vault) external returns (address proxy) {
    
    // Proxy is set as a clone of the instance of the BeefyWrapper contract.
    proxy = implementation.clone();
    
    // Initializes the wrapper proxy set above.
    IWrapper(proxy).initialize(
        _vault,
        string.concat("W", IVault(_vault).name()),
        string.concat("w", IVault(_vault).symbol())
    );
    
    // Emits the ProxyCreated event to signify a successful deployment.
    emit ProxyCreated(proxy);
}
```

## Contratos

Os contratos embrulhadores modelo cofre da Beefy são mantidos publicamente nos repositórios GitHub da Beefy. Consulte [BeefyWrapper.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyWrapper.sol) e [BeefyWrapperFactory.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyWrapperFactory.sol).

Os contratos embrulhadores para cada cofre da Beefy serão lançados separadamente nas redes relevantes e não serão necessariamente implantados em endereços de contrato semelhantes. Para testar exemplos de contratos implantados na blockchain Polygon, consulte esta instância do [BeefyWrapper.sol](https://polygonscan.com/address/0x776994eab59b894fb892d08a46329c5077c9e226) e esta instância do [BeefyWrapperFactory.sol](https://polygonscan.com/address/0xd1cedfb11994ebbc1608ae46d7c7176294bdd599).
