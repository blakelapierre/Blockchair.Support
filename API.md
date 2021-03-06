# [Blockchair.com](https://blockchair.com/) API

### API v.2 documentation
* English: [API_DOCUMENTATION_EN.md](API_DOCUMENTATION_EN.md).
* Russian: [API_DOCUMENTATION_RU.md](API_DOCUMENTATION_RU.md).

### Changelog

* v.2.0.13 - Feb 13th - Added support for Cyrillic characters in fulltext search, e.g. `https://api.blockchair.com/bitcoin/outputs?q=script_bin(~привет)`
* v.2.0.12 - Feb 12th - Fixed a bug in Ethereum where some contract creations were erroneously shown as failed (thanks Daniel Luca for noticing) 
* v.2.0.11 - Feb 5th
    * We're changing behavior of our `mempool` tables (for all supported coins except for Ethereum): now they don't contain the contents of the latest block (it was quite a clumsy thing to have both mempool transactions and transactions from the latest block in this table, but we've rebuilt our engine, so now `mempool` tables contain mempool content only, and it finally makes sense!). That means:
        * `{chain}/mempool/blocks` is deprecated. Hint: if you used `mempool/blocks` to get info about the latest block you can simply switch to using `blocks?limit=1`, e.g. `https://api.blockchair.com/bitcoin/blocks?limit=1`
        * `{chain}/mempool/transactions` and `{chain}/mempool/outputs` now don't contain info from the latest block, while `{chain}/transactions` and `{chain}/outputs` do
        * Before this update when using (undocumented) `export` functionality there was no information about the latest block at all, now there is
        * The same change to Ethereum will come in one of the next updates
    * Dogecoin is out of beta.
    * Bitcoin SV is out of beta. Please note there's still a possibility that we won't be able to offer some functionality in the long term if blocks suddenly become larger than 1 exabyte, we're still waiting for a more clear development roadmap.
* v.2.0.10 - Jan 29th, 2019 - Added Dogecoin support in test mode (see `Dogecoin support` in the docs)
* v.2.0.9 - Dec 13th - Added Bitcoin SV support in test mode (see `Bitcoin SV support` in the docs); updated aggregation abilities (see `Data aggregation support` in the docs)
* v.2.0.8 - Nov 26th - Added the ability to retrieve raw transaction data in hex, see `Retrieving raw transactions` in the docs
* v.2.0.7 - Nov 22th - Now it's possible to broadcast transactions using our API, see `Broadcasting transactions` in the docs
* v.2.0.6 - Oct 8th - Added data aggregation of blockchain data in beta mode, see `Data aggregation support` in the docs
* v.2.0.5 - Oct 8th - Fixed bug where `balance` and `received` for bitcoin[-cash]|litecoin addresses in the `{chain}/dashboards/address/{address}` call were calculated wrong if there were specific unconfirmed transactions
* v.2.0.4 - Oct 3rd - Added some new useful fields to `{chain}/stats` calls
* v.2.0.3 - Sep 18th - Added `context.api.tested_features` with the list of features our API supports, but with no guarantee for backward compatibility if updated. Added Omni Layer and Wormhole support in testing mode (see "Tested features changelog")
* v.2.0.2 - Sep 9th - Added `address.contract_created` to the `ethereum/dashboards/address/{A}` call
* v.2.0.1 - Sep 1st, 2018 - Added Litecoin support
* v.2.0.0 - Migrating from API v.1 to API v.2 (see the docs)

### Support

* E-mail: [info@blockchair.com](mailto:info@blockchair.com)
* Telegram chat: [@Blockchair](https://telegram.me/Blockchair)
* Twitter: [@Blockchair](https://twitter.com/Blockchair)
