# Data
Data used in the project



## `data_assets_dictionary.xlsx`

**Basic Security Identifiers**     
- `isin`: International Securities Identification Number - unique identifier for the security
- `cusip`: Committee on Uniform Securities Identification Procedure number 
- `assetId`: Internal asset identifier
- `figId`: Another internal identifier system

**Security Characteristics**
- `ccy`: Currency (USD in all cases shown)
- `cpn`: Coupon rate (annual interest rate)
- `maturity`: Maturity date of the bond
- `secType`: Security type (CORP = corporate bonds)
- `secGroup`: Security group (BND = bonds)

**Risk Metrics (Key Rate Durations)**
These measure sensitivity to interest rate changes at different maturity points:
- `krd3m`, `krd1y`, `krd2y`, `krd3y`, `krd5y`, `krd7y`, `krd10y`, `krd15y`, 
  `krd20y`, `krd25y`, `krd30y`, `krd40y`, `krd50y`:  Key rate durations
   for different time horizons

**Spread and Duration Metrics**
- `oad`: Option-adjusted duration
- `oas`: Option-adjusted spread (in basis points)
- `spreadDur`: Spread duration 
- `dxs`: Credit spread duration

**Issuer Information**    
- `issuerId`: Unique issuer identifier
- `issuerLongName`: Full company name
- `issuerShortName`: Abbreviated name
- `issuerTicker`: Trading ticker symbol
- `issuerCountry`: Country of issuer
- `countryRisk`: Country risk classification

**Trading Information**
- `price`: Current market price
- `minTradeSize`: Minimum trade size in units
- `minTradeIncrement`: Minimum increment for trading

**Portfolio Positions**
- `fund_posQuantity`: Current position quantity in the fund
- `bench_posQuantity`: Benchmark position quantity
- `fund_enriched.mktValue`: Market value of fund position
- `fund_enriched.notionalMktValue`: Notional market value

**Cash Ladder Projections**
Columns showing projected cas balance at different time horizons:
- `enriched.cashladder_tCashBalance` through `enriched.cashladder_tPlus90CashBalance`

**Portfolio Analytics**   
- `fund_enriched.pmv`: Portfolio market value percentage
- `fund_enriched.dc`: Duration contribution
- `fund_enriched.dxsCtr`: Spread duration contribution
- Various `krdXXCtr` columns: Key rate duration contributions


**Relative Value Metrics**   
- `enriched.tsyRV`: Treasury relative value metrics
- `enriched.creditRV`: Credit relative value signals and Z-scores
- `enriced.MktxLiqScore`: Liquidity score

**Classification Hierarchies**
- `sodraw.filterLevel1-4`: Various classification levels (Investment Grade 
  Credit, Financial, Insurance, etc.)
- `sodraw.pathVngcore` and `sodraw.pathHUBGLOB`: Additional classification 
  paths

**Creadit Quality**   
- `enriched.creditQualityBuckets`: Credit quality classificaiton
- `security.elements.normalizedRating`: Standardized credit rating (A, BBB, etc.)

**Other Key Columns**   
- `portfolioName`: Name of the portfolio (VCIT in examples)
- `strategyName`: Trading strategy designation
- `fund_orderStatus`: Order status for the position
- `posSource`: Position source (EOD = End of Day)