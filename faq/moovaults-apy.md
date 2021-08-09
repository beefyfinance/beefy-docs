# mooVaults APY

## What is the APY?

Let's look at a typical yield farm, where they state an APY \(annual percentage yield\) as +100% for example. The traditional definition of APY _**is the real rate of return earned on an investment taking into account the effect of compounding earnings**_. Using this terminology would indicate that the yield farm was compounding earnings for you. That is simply not the case. A more applicable terminology to use would be APR \(annual percentage rate\), meaning the annual rate earned through an investment. By definition this would mean that your 100% yield farm would double your original investment at the end of year 1 without reinvesting any earnings. But what about if you reinvested that entire amount the next year and the year after that?

## Understanding Exponential Growth \(Compounding\)

Growth whose rate becomes ever more rapid in proportion to the growing total number or size. The simple formula for this is _**growth = \(1 + r\)^x**_ , where 'r' = return and 'x' = number of 'times'. For example, your money doubles every year if you get 100% yearly return. After 3 years you would have 8x your original investment.

![growth = \(1 + 100%\)^3](../.gitbook/assets/capture%20%282%29.png)

## Ok, so what REALLY is the APY?

A typical investment does not just pay out on a yearly basis, but in smaller terms \(ie: daily, monthly, etc\). For yield farming, returns are even paid out on a per block basis. With an average of 28,800 blocks a day and cheap transaction fees this can allow for a significant amount of exponential growth or compounding of your return. Let's look at how to break that down...

* Compound = **P \* \(1+r/n\)^nt**                Example : 100 \* \(1+1/12\)^\(12\*1\)
* P = principal or starting balance
* r = APR = 100%
* n = compounding periods = 12 months
* t = time = 1 year
* The simple APY calculation in excel can also be stated as =EFFECT\(r, n\)

![Year 1 end would be 261 tokens or 161% APY versus 100% APR w/o compounding](../.gitbook/assets/capture%20%283%29.png)

