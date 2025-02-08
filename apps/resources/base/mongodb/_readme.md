# Configuration

Create a username password pair for the MongoDB database and export the values as base64 encoded strings as environment variables.

```bash
export MONGO_USERNAME=$(echo -n 'adminuser' | base64)
export MONGO_PASSWORD=$(echo -n 'password123' | base64)
```
