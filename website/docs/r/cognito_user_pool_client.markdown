layout: "aws"
page_title: "AWS: aws_cognito_user_pool_client"
side_bar_current: "docs-aws-resource-cognito-user-pool-client"
description: |-
  Provides a Cognito User Pool Client resource.

# aws_cognito_user_pool_client

Provides a Cognito User Pool Client resource.

## Example Usage

### Create a basic user pool client client

```hcl
resource "aws_cognito_user_pool" "pool" {
  name = "pool"
}

resource "aws_cognito_user_pool_client" "client" {
  name = "client"
  
  user_pool_id = "${aws_cognito_user_pool.pool.id}"
}
```

### Create a user pool client with no SRP authentication
```hcl
resource "aws_cognito_user_pool" "pool" {
  name = "pool"
}

resource "aws_cognito_user_pool_client" "client" {
  name = "client"

  user_pool_id = "${aws_cognito_user_pool.pool.id}"

  generate_secret = true
  explicit_auth_flows = ["ADMIN_NO_SRP_AUTH"]
}
```

## Argument Reference

The following arguments are supported:

* `allowed_oauth_flows` - (Optional) List of allowed OAuth flows (code, implicit, client_credentials).
* `allowed_oauth_flows_user_pool_client` - (Optional) Whether the client is allowed to follow the OAuth protocol when interacting with Cognito user pools.
* `allowed_oauth_scopes` - (Optional) List of allowed OAuth scopes (phone, email, openid, Cognito).
* `callback_urls` - (Optional) List of allowed callback URLs for the identity providers.
* `default_redirect_uri` - (Optional) The default redirect URI. Must be in the list of callback URLs.
* `explicit_auth_flows` - (Optional) List of authentication flows (ADMIN_NO_SRP_AUTH, CUSTOM_AUTH_FLOW_ONLY).
* `generate_secret` - (Optional) Should an application secret be generated. AWS JavaScript SDK requires this to be false.
* `logout_urls` - (Optional) List of allowed logout URLs for the identity providers.
* `name` - (Required) The name of the application client.
* `read_attributes` - (Optional) List of user pool attributes the application client can read from.
* `refresh_token_validity` - (Optional) The time limit in days refresh tokens are valid for.
* `supported_identity_providers` - (Optional) List of provider names for the identity providers that are supported on this client.
* `user_pool_id` - (Required) The user pool the client belongs to.
* `write_attributes` - (Optional) List of user pool attributes the application client can write to. 

## Attribute Reference

The following attributes are exported:

* `id` - The id of the user pool client.
* `client_secret` - The client secret of the user pool client.
