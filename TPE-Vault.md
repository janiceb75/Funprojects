## TPE-VAULT ##


Lastpass has been deprecated and as a replacement, we are now using Broadcom's production grade instance of Vault.

The URL for Vault is located [here](https://tpe-vault-rock.eng.vmware.com).

## Here are the steps for accessing the secrets that were migrated over from LastPass:

1. Click on the URL for Vault
2. Select "LDAP" as the Method
3. Enter your Broadcom username and password
4. Select the "secret-operability" engine
5. Select the folder "lastpass-migration" and then the particular folder you are looking for, for example "Shared-TAS-Operability"

## Accessing the One-Time passcode

The Tas-Operability-Bot account requires a one-time passcode in order to gain access to Github.  The steps to receive this passcode in Vault requires the use of the Vault CLI. The steps are below:

1. Ensure that Vault is installed on your local machine so that you can utilize the CLI.  Refer to the [Vault docs](https://developer.hashicorp.com/vault/tutorials/getting-started/getting-started-install) for specific instructions. If you are running a Mac, you can install via Homebrew by running:
   ```
   brew install vault
   ```
2. To confirm that Vault was installed correctly, run
   ```
   vault --version
   ```
3. Set the Vault address to the team instalnce of vault by running:
   ```
   export VAULT_ADDR=https://tpe-vault-rock.eng.vmware.com
   ```
4. Run "vault status" to confirm
5. Login to Vault:
   ```vault login
   ```
6. You will be prompted to enter your token. You will have to be logged into Vault via the URL first. This will enable you to click on the person icon in the upper left corner and choose "Copy Token".
7. Enter this token at the command prompt
8. Once you have successfully been authenticated via the command line, enter the following:
   ```
   vault read totp/code/tas-operability-github
   ```
9. You should get a 6 digit code to use when you are prompted by Github for the 2-factor authentication code.
