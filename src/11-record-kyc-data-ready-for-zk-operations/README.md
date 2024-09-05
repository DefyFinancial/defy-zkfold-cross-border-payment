# Recording of user's data for ZKP

In this stage, our main focus in on recording the user's data, in a specific format that will be used for the ZK operations.

To simplify the problem, we will not deal with permissions, access control, or any other security-related issues. We will focus on the data format and how to store it, so that it can be retrieved and used for the later ZK pipelines.

## System process

1. User will go through the KYC process, they will answer each questions to fill up their personal data (birthdate, citizenship, etc).
2. Upon completion of the KYC process, the data gone though a vendor to verify the data correctness matching the user's documents (imagine OCR checking if the ID matches the one on passport)
3. The backend will send `value` to a "ZK" service to hash the value and return the `hash` value
4. Each data field (e.g. birthdate) are store one the private blockchain, as a token, with the following fields:
    - `type`: the type of the data (e.g. birthdate)
    - `value`: the encrypted value of the data (e.g. 1990-01-01 -> `encrypted(value)`)
    - `hash`: the hash of the data that is stored in the format for the ZK operation (e.g. `hash(encryptedvalue)`)
    - `id`: the id of the data so that it can be retrieved later

## Data types for ZK operations

- `numeric` in range: `age`, `income`
  - allow proving that a value lies within a certain range
  - For example, proving user age is between 18-65. Is age > 18 (False = flag orange)
  - For example, proving user income is between 1000-5000

- `string` in set: `citizenship/nationality`, `country of birth`, `address`, `business type`
  - prove that an element belongs to a predefined set without revealing which specific element it is
  - For example, proving user's country of birth is in the list of approved countries
  - For example, proving user's citizenship/nationality is in the list of approved countries. Is the country part of (sanction) list (Yes = flag red)
  - For example, proving user's place of residence (the country or state) is in the list of approved countries
  - For example, proving user's business type is in the list of approved business types

- `string` is equal
  - demonstrate that two values are equal without revealing what those values are
  - Country of birth = nationality (False = flag orange)

- `string` not in set
  - similar to `string in set` but the opposite

- `string` is not equal
  - similar to `string is equal` but the opposite

## Sample data

From the product application, a set of user data will be collected from the user.

In order to split the data into different parts to store in different tokens, we could use the following structure.

For birthdate (yyyy-mm-dd):

```json
{
  "type":"birthdate",
  "value":"1990-01-01"
}
```

Since we care about age, we need to derive the age from the birthdate. Maybe hashing the year of birth is enough for the ZK operations?

For citizenship (ISO 3166-1 alpha-2):

```json
{
  "type":"citizenship",
  "value":"FR"
}
```

This should able to expanded other similar fields such as `address` (e.g. country; we can expand to state and others in future)

## Expected output

A set of scripts (written in TypeScript) are expected to be developed to store the data in a specific format suitable for the ZK operations.

This script should be able to:
- given a `data` field (e.g. birthdate), hash the value with the algorithm suitable for ZK curve
- the `hash` should be returned to the caller (could be an API if it lives in another machine or a function call)

These scripts should be written in TypeScript for integration with the product application
