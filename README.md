اسکریپت Allora برای دوستانی که قبلا ران کرده بودن و میخوان آپدیت کنن
```
cd
rm -rf allora.sh 
wget https://raw.githubusercontent.com/cryptoneth/Allora-Script-/main/allora.sh && chmod +x allora.sh && ./allora.sh
```
مراحل رو دونه دونه جلو برید 
** جایگذاری های Head ID + Recovery Phrase و ... مشخص هست


==========================================================================

اسکریپت Allora برای دوستانی که جدید میخوان ران کنن کلا 

```
cd
rm -rf alloranew.sh 
wget https://raw.githubusercontent.com/cryptoneth/Allora-Script-/main/alloranew.sh && chmod +x alloranew.sh && ./alloranew.sh
```
* جایگذاری های Head ID + Recovery Phrase و ... مشخص هست

==========================================================================

کامند سلامت نود 1 : 
```
network_height=$(curl -s -X 'GET' 'https://allora-rpc.testnet-1.testnet.allora.network/abci_info?' -H 'accept: application/json' | jq -r .result.response.last_block_height) && \
curl --location 'http://localhost:6000/api/v1/functions/execute' --header 'Content-Type: application/json' --data '{
    "function_id": "bafybeigpiwl3o73zvvl6dxdqu7zqcub5mhg65jiky2xqb4rdhfmikswzqm",
    "method": "allora-inference-function.wasm",
    "parameters": null,
    "topic": "1",
    "config": {
        "env_vars": [
            {
                "name": "BLS_REQUEST_PATH",
                "value": "/api"
            },
            {
                "name": "ALLORA_ARG_PARAMS",
                "value": "ETH"
            },
            {
                "name": "ALLORA_BLOCK_HEIGHT_CURRENT",
                "value": "'"${network_height}"'"
            }
        ],
        "number_of_nodes": -1,
        "timeout": 3
    }
}' | jq
```

امند سلامت نود 2 : 

```
network_height=$(curl -s -X 'GET' 'https://allora-rpc.testnet-1.testnet.allora.network/abci_info?' -H 'accept: application/json' | jq -r .result.response.last_block_height) && \
curl --location 'http://localhost:6000/api/v1/functions/execute' --header 'Content-Type: application/json' --data '{
    "function_id": "bafybeigpiwl3o73zvvl6dxdqu7zqcub5mhg65jiky2xqb4rdhfmikswzqm",
    "method": "allora-inference-function.wasm",
    "parameters": null,
    "topic": "2",
    "config": {
        "env_vars": [
            {
                "name": "BLS_REQUEST_PATH",
                "value": "/api"
            },
            {
                "name": "ALLORA_ARG_PARAMS",
                "value": "ETH"
            },
            {
                "name": "ALLORA_BLOCK_HEIGHT_CURRENT",
                "value": "'"${network_height}"'"
            }
        ],
        "number_of_nodes": -1,
        "timeout": 3
    }
}' | jq
```


