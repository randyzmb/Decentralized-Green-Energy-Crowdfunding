# Decentralized-Green-Energy-Crowdfunding
構築WEB3ベースのプラットフォームにより、個人が再生可能エネルギープロジェクトにクラウドファンディングを行い、持続可能な未来を促進することができます。
from web3 import Web3
import json

# Connect to an Ethereum node
w3 = Web3(Web3.HTTPProvider('https://infura.io/v3/YOUR_INFURA_PROJECT_ID'))

# Contract details (replace with actual values after deploying the contract)
contract_address = '0xYourContractAddress'
contract_abi = json.loads('YourContractABI')

# Setup contract object
contract = w3.eth.contract(address=contract_address, abi=contract_abi)

def create_project(name, goal, from_address):
    tx_hash = contract.functions.createProject(name, goal).transact({'from': from_address})
    receipt = w3.eth.waitForTransactionReceipt(tx_hash)
    return receipt

def contribute_to_project(project_id, amount, from_address):
    tx_hash = contract.functions.contributeToProject(project_id).transact({'from': from_address, 'value': amount})
    receipt = w3.eth.waitForTransactionReceipt(tx_hash)
    return receipt

# Example usage (Ensure you have the correct from_address and have enough Ether for contributions)
# create_project('Solar Power Initiative', 5 * 10**18, '0xYourWalletAddress')
# contribute_to_project(0, 1 * 10**18, '0xYourWalletAddress')
