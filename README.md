# project1
source <(curl -s https://raw.githubusercontent.com/nodejumper-org/cosmos-scripts/master/lava/lava-testnet-1/install.sh)

——————
#create wallet :
———————-


lavad keys add wallet


———————————-
 #SAVE SEED PHRASE 
——————————
#SAVE PRIVATE VALIDATOR KEY :
—————————————-

cat $HOME/.lava/config/priv_validator_key.json

——————————
#wait util the node is synced, should return FALSE
———————————-

#For check synce :
————————————

lavad status 2>&1 | jq .SyncInfo.catching_up

faucet : 
ask in discord, 

——————————
#Check balance :
———————————-

lavad keys show wallet -a

lavad q bank balances $<lavad keys show wallet -a>

______________________
 #create validator :
__________________________


lavad tx staking create-validator \
--amount=90000ulava \
--pubkey=$(lavad tendermint show-validator) \
--moniker="YOUR_VALIDATOR_MONIKER" \
--chain-id=lava-testnet-1 \
--commission-rate=0.1 \
--commission-max-rate=0.2 \
--commission-max-change-rate=0.05 \
--min-self-delegation=1 \
--fees=10000ulava \
--from=wallet \
-y

—————————-
#you can see the validator details :
—————————————————-

lavad q staking validator $(lavad keys show wallet --bech val -a)


✅Minimum Hardware Requirements 
3CPU 4RAM 80GB
