# deploy-aleo
aleo deploy
aleo smart contract


Install prerequisites
------------------------------------------------------------------
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

source $HOME/.cargo/env

rustup install stable

rustup update stable

rustup default stable

git clone https://github.com/AleoHQ/leo
cd leo

apt install clang gcc libssl-dev pkg-config

cargo install --path .

git clone https://github.com/AleoHQ/snarkOS.git --depth 1
cd snarkOS

./build_ubuntu.sh

cargo install --path .

//faucet site 
------------------------------------------------------------------

https://faucet.aleo.org/
Text 📱 +1-867-888-5688 with "Send 50 credits to aleo1xxxxxx"

----------------------------------------------------------------------------
//After receiving Faucet, go to the link below and add the extension to the Chrome browser

https://chrome.google.com/webstore/detail/json-beautifier-editor/lpopeocbeepakdnipejhlpcmifheolpl
------------------------------------------------------------------

cd $HOME

mkdir demo_deploy_Leo_app && cd demo_deploy_Leo_app

WALLETADDRESS=""     //Put your wallet address between ""

APPNAME=helloworld_"${WALLETADDRESS:4:6}"

leo new "${APPNAME}"

PATHTOAPP=$(realpath -q $APPNAME)

cd $PATHTOAPP && cd ..

PRIVATEKEY=""

RECORD=""

snarkos developer deploy "${APPNAME}.aleo" --private-key "${PRIVATEKEY}" --query "https://vm.aleo.org/api" --path "./${APPNAME}/build/" --broadcast "https://vm.aleo.org/api/testnet3/transaction/broadcast" --fee 600000 --record "${RECORD}"


