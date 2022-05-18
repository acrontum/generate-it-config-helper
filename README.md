# openapi-nodegen-config-helper

![test](https://github.com/acrontum/openapi-nodegen-config-helper/workflows/test/badge.svg)

Used within the generate-it but easily used in other tools. Ensure environment variables are set or if not with a default value.

Return process variables to bool/number/object/string/undefined/null based on the value provided. See the index.js returnValue for more.

## Available helpers

Method: withDefault
```
import ConfigHelper from 'openapi-nodegen-config-helper';
ConfigHelper.withDefault('SWAGGER_FILE', 'latest')
```

Method: required
```
import ConfigHelper from 'openapi-nodegen-config-helper';
ConfigHelper.required('JWT_SECRET')
```

## withDefault adds a new process.env 

## Example
```typescript
import dotenv from 'dotenv';
import ConfigHelper from 'openapi-nodegen-config-helper';
import someHelper from './helpers/someHelper';

dotenv.config();

export default {
  // Swagger file
  swaggerFile: ConfigHelper.withDefault('SWAGGER_FILE', 'latest'),
  jwtSecret: ConfigHelper.required('JWT_SECRET'),

  port: ConfigHelper.withDefault('PORT', 666),
  
  somethingElse: someHelper(process.env.CONFIG_HELPER_PORT), // CONFIG_HELPER_PORT is injected into the process.env and can be accessed this way 
  somethingOther: someHelper(process.env.CONFIG_HELPER_JWT_SECRET), // CONFIG_HELPER_JWT_SECRET is injected into the process.env and can be accessed this way 
}
```
