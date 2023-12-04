# About

This is Profiles library project to create user features from Shopify event stream tables created using Rudderstack SDK


# Inputs
## Raw Tables
| name | table | path |
| ---- | ----- | ---- |
| rsIdentifies | IDENTIFIES | RUDDERSTACK_TEST_DB.DATA_APPS_SIMULATED_SHOPIFY.IDENTIFIES |
| rsTracks | TRACKS | RUDDERSTACK_TEST_DB.DATA_APPS_SIMULATED_SHOPIFY.TRACKS |
| rsPages | PAGES | RUDDERSTACK_TEST_DB.DATA_APPS_SIMULATED_SHOPIFY.PAGES |


# Identity Stitching
## user identities
| name | exclusions | sourced_from |
| ---- | ---------- | ------------ |
| user_id |  | ["rsIdentifies:user_id","rsTracks:user_id","rsPages:user_id"] |
| anonymous_id | unknown, NaN | ["rsIdentifies:anonymous_id","rsTracks:anonymous_id","rsPages:anonymous_id"] |
| email | test@company.com | ["rsIdentifies:lower(email)"] |
# Features

## user features
| Feature | Computed From | Description |
| ------- | ------------- | ----------- |
| days_since_account_creation | rsIdentifies |  |
| days_since_last_seen |  |  |
| is_churned_7_days |  | it specifies if there is any activity observed in the last n days. It is dependent on days_since_last_seen |
