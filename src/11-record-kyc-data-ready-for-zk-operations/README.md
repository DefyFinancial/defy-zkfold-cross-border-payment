# Recording of user's data

In this stage, our main focus in on recording the user's data, in a specific format that will be used for the ZK operations.

To simplify the problem, we will not deal with permissions, access control, or any other security-related issues. We will focus on the data format and how to store it.

## Sample data

From the product application, data will be collected from the user.

In order to split the data into different parts, we could use the following structure.

For birthdate:

```json
{
  "type":"birthdate",
  "value":"1990-01-01"
}
```

For citizenship:

```json
{
  "type":"citizenship",
  "value":"FR"
}
```

## Expected output

A set of scripts are expected to be developed to store the data in a specific format suitable for the ZK operations.

These scripts should be written in TypeScript for integration with the product application.
