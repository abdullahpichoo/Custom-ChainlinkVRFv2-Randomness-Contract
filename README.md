# Chainlink VRFv2 Random Number Contract with Custom Python Script
A project where I receive random numbers from the Chainlink VRF Node in my contract and automate the process using Python

# How ChainLink VRFv2 Works:
The Chainlink VRFv2 is Subscription Based and here's how you can get a Random Number:
- Create a Subscription
- Fund that Subscription with Sufficient LINK
- Add your contract as a Consumer to the Subscription so that the Chainlink Node can return a Random Number to it.
- Cancel your Subscription when you're done and the remaining LINK will be returned to your wallet.

# How I Coded it
There were some hardcoded snippets on the ChainLink website for the VRFv2 and how to get random numbers using it, but it would take someone new quite some time to understand. Now here's how I made Lottery Version 2:
## Making a Contract that manages and creates subscriptions
- I used the Subscription Manager contract on the ChainLink website and modified it into something more robust with custom parameters.
- The contract will take 3 parameters in its constructor:
   - VRFCoordinatorV2 Address
   - Link Token Address
   - Key Hash
- The contract has pretty self-explanatory functions and taking a look at it will give you a good idea of the role of each function.
### Here's how I changed the Lottery Contract
- I got rid of all the random number request functions and made this contract into a pure lottery contract.
- Made a new function ```chooseWinner``` that takes a random number as a parameter.
- The Lottery will then choose a winner, transfer the funds to their address and end the Lottery.
### How to get the Random Number?
I made a separate script that automates the retrieval of random numbers. Here's what the script does:
- It deploys the custom VRFv2
- It creates a new subscription
- It funds the subscription with some LINK
- It adds itself as a Consumer so that it can receive a random number.
- It receives the random number and stores it and it can be returned.
All of this process is automated through a single function and can also be done through a menu interface if you want to see it's working.

### DeployV2 Script
The only change I made in the deploy script is that it imports the ```get_random``` function from the ```deploy_VRFv2``` script and stores the returned random number in a variable. It then passes the random number to the ```chooseWinner``` function and concludes the Lottery.

That's all. I hope this can help someone out as I really struggled with this and it would be a win for me if a fellow programmer could benefit from what I've done here.
Cheers!

