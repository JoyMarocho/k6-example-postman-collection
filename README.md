## JSON-TO-K6

This repository contains an exported Postman collection and its converted k6 script for demonstration in [the Postman article in our blog](https://k6.io/blog/load-testing-with-postman-collections).

## K6 - Load Testing Our Test API with The Postman Collection
**1. Optional: Clone the repository and skip to the step 5:**
        `git clone https://github.com/JoyMarocho/k6-example-postman-collection.git`

**2. Install Node.js (if you haven't already done so), For Windows Users Follow the steps in the link shared**
        - [https://www.geeksforgeeks.org/how-to-install-and-use-nvm-on-windows/](#Windows-Users)

        Confirm NVM is installed successfull: `nvm -v`

**3. Install the postman-to-k6 tool:**
- The postman-to-k6 tool is developed to help you convert the requests inside your Postman collections to k6 scripts, which are actually JavaScript code.
        ```shell
        $ npm install -D @apideck/postman-to-k6
        ```

        or using yarn...

        ```shell
        $ yarn add @apideck/postman-to-k6
        ```

Note that this will require you to run the converter with `npx @apideck/postman-to-k6 your-postman-file` or, if you are
using an older versions of npm, `./node_modules/.bin/postman-to-k6 your-postman-file`.

### Global Installation

        ```shell
        $ npm install -g @apideck/postman-to-k6
        ```

- If you encounter any issues run this command then repeat the above command.
        `npm config set strict-ssl false`

- If you encounter any issues with uuid run this command then repeat this npm install -g @apideck/postman-to-k6 command.
        `npm install uuid@7.0.3 --force`


**4. Convert your exported Postman collection to k6 script:**
- Assuming your exported collection is named `test-api.json`, you can run this command to convert it to a k6 script. The `env.json` includes 
all your environment variables that are exported from Postman.
        ```shell
        $ postman-to-k6 collection.json -o k6-script.js
        ```

Then run the script in k6, as usual, using:

        ```shell
        $ k6 run k6-script.js
        ```

## JMETER-to-K6
-------------------------------------------------------------

**Install**:

Globally, and preferably using [nvm](https://github.com/creationix/nvm) (at least on Unix/Linux systems to avoid filesystem permission issues when using sudo):

```shell
npm install -g jmeter-to-k6
```

Locally, into `./node_modules`:

```shell
npm install jmeter-to-k6
```

Note that this will require you to run the converter with `node node_modules/jmeter-to-k6/bin/jmeter-to-k6.js ...`.

Alternatively, you can install the tool from DockerHub:

```shell
docker pull loadimpact/jmeter-to-k6
```

**Convert**:

Convert [JMeter](https://jmeter.apache.org/) JMX to [k6](https://k6.io/) JS.

```shell
jmeter-to-k6 example/full.jmx -o full
```

This will create a directory `./full/` with a file called `test.js` and a sub-directory called `libs`.

One-off execution using [npx](https://www.npmjs.com/package/npx) (avoiding the installation of the tool on your system):

```shell
npx jmeter-to-k6 example/full.jmx -o full
```

Using the Docker image, you execute the tool as follows:

```shell
docker run -it -v "/path/to/jmeter-files/:/output/" loadimpact/jmeter-to-k6 /output/MyTest.jmx -o /output/MyTestOutput/
```

and then execute the k6 test using:

```shell
k6 run /path/to/jmeter-files/MyTestOutput/test.js
```

**Run test in k6**:

```shell
k6 run full/test.js
```
