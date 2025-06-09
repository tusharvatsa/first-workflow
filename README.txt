Steps Required to move config from DEV to TEST
===================================================
1. under /config there exists 2 files
   config-dev-to-test-sync.json : consists of the security systems, endpoints and connections that you want to move from dev to test
   config-valid-attributes      : provides the mapping of any attribute per items being moved that can be either
   1. excluded - thse are key value pairs you want to exclude from DEV config and not push to TEST
   2. overrde  - these are key value pairs that you want to add/update in source JSON before pushing to target

2. Limitations
   Following configurations are not moved by this workflow
   - EP Dynamic attributes
   - EP entitlement_types or their configuration
   - Email templates   - must be present in the target before they can be added (this does not move email templates)
   - Password policies - must be present in the target before they can be added (this does not move the password policies) 
   - Entitlements with new account 
   - Data - Accounts/Entitlements

3. Recommendations
   - Keep the names of SS/EP/Connections same in all environments
   
   
4. Possible imporovements
	- Credentials of connections to be taken from GitHub Secrets instead of configuration / override
	- brancing strategy to keep dev, test, prod config in github 
    - approval workflows in github to approve/reject merge requests
    - ability to push specific configuration to specific env for eg dev	

5. Edge cases
	- Entitlements_Only
	- Dependent endpoint