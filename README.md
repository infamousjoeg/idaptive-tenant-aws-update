# IDaptive Tenant AWS Update

Created in Bash, this script will get your IDaptive Tenant's current IP Address and checks a pertinent AWS Security Group for the IDaptive Tenant's allowed access over port 443. If it does not exist, it will update the AWS Security Group for IDaptive Tenant access over port 443.

_Use this script if you do not feel comfortable allowing all potential AWS EC2 instance IP Address blocks._

## Requirements

* [AWS CLI](https://aws.amazon.com/cli/)
* [IDaptive Tenant](https://www.idaptive.com/free-trial)

## How it works

1. The `IDAPTIVE_TENANT_URL` is used to `dig` the IP Address currently assigned.
2. Using the AWS CLI, the defined AWS Security Group is described to list all current `CidrIP`s allowed to ingress over port 443.
3. The `IDAPTIVE_TENANT_IP` is checked against the list returned in Step 2.
   1. If the `IDAPTIVE_TENANT_IP` already exists, it exits with a zero (0) code.
   2. If the `IDAPTIVE_TENANT_IP` does not exist, the script continues.
4. If the script didn't exit in Step 3, it adds the `IDAPTIVE_TENANT_IP` to the AWS Security Group and exits.

## Usage

1. Open the `idaptive-update` script in an editor.
2. Change the values of the two (2) variables labeled `# CHANGE ME` to match your environment.
3. Execute the script `idaptive-update`.

## Maintainer

Joe Garcia - [@infamousjoeg](https://github.com/infamousjoeg)

[![Buy me a coffee][buymeacoffee-shield]][buymeacoffee]

[buymeacoffee]: https://www.buymeacoffee.com/infamousjoeg
[buymeacoffee-shield]: https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png

## License

[MIT](LICENSE)
