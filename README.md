## About

This repository contains an exported Postman collection and its converted k6 script for demonstration in [the Postman article in our blog](https://k6.io/blog/load-testing-with-postman-collections).

## K6 - Load Testing Our Test API with The Postman Collection
**1. Optional: Clone the repository and skip to the step 5:**
        - `git clone https://github.com/JoyMarocho/k6-example-postman-collection.git`

**2. Install Node.js (if you haven't already done so), For Windows Users Follow the steps in the link shared**
        - [https://www.geeksforgeeks.org/how-to-install-and-use-nvm-on-windows/](#Windows-Users)

        Confirm NVM is installed successfull: `nvm -v`

**3. Install the postman-to-k6 tool:**
- The postman-to-k6 tool is developed to help you convert the requests inside your Postman collections to k6 scripts, which are actually JavaScript code.
        `npm install -g @apideck/postman-to-k6`

- If you encounter any issues run this command then repeat the above command.
        `npm config set strict-ssl false`

- If you encounter any issues with uuid run this command then repeat this npm install -g @apideck/postman-to-k6 command.
        `npm install uuid@7.0.3 --force`


**4. Convert your exported Postman collection to k6 script:**
- Assuming your exported collection is named `test-api.json`, you can run this command to convert it to a k6 script. The `env.json` includes 
all your environment variables that are exported from Postman.
        `postman-to-k6 test-api.json -e env.json -o k6-script.js`