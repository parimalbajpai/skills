---
name: coinswitch-statement-analysis
description: Analyze crypto transaction statement from Coinswitch Kuber. 
---

# Crypto profit loss analysis

Make sense of Coinswitch statement sheet.

## Input Requirements

Expects campaign data in CSV format with these columns:

 -- **Transaction Id**
 -- **Date**
 -- **Market**
 -- **Price**
 -- **Volume**
 -- **Total**
 -- **Trade Type**
 -- **TDS Amount**
 -- **TDS Paid In**
 -- **TDS In INR**
 -- **Fee Paid In**
 -- **Fee Amount**

## Column explanation

  **Date**: Is time in YYYY-MM-DD format and time of the day.
  **Market**: Is the crypto name prefix with currency suffix. For e.g. BTCINR is BTC crypto described in INR currency.
  **Price**: Is per unit price of the crypto in the mentioned currency. Remove currency suffix to get the correct numerical value.
  **Volume**: Is quantity of crypto traded.
  **Total**: Is product of Price and Volume.
  **Trade Type**: Is buy or sell operation.
  TDS in all columns refers to tax deduction.
  Fee in all columns is platform fee charged on the transaction.

## Analysis

Calculate one table per Market: 
- create one row per year
- for all BUY: COST = sum of Total + TDS + Fee
- COST-UNITS = sum of all units under BUY 
- for all SELL: GAIN = sum of Total - TDS - Fee 
- SELL-UNITS = sum of all units under SELL

## Output Format

Present results as tables with status indicators:

**COST - SELL Analysis**
| Year | Crypto | COST | COST-UNITS | COST / COST-UNITS | SELL | SELL-UNITS | SELL / SELL-UNITS

