---
uid: ccUsers
---
# Users

A user is an identity that has access to an OSIsoft Cloud Services (OCS) tenant. Roles assigned to a user determine what permissions the user has on resources in OCS. For more information on roles, see [About Roles](xref:ccRoles). Users must be linked to a tenant from an enabled identity provider such as Azure Active Directory, Microsoft Accounts, or Google. Users log in to OCS using the credentials from that account.

Users log in through a user account  into the [OCS Portal](https://cloud.osisoft.com), and users authenticate when using [Hybrid Clients](xref:ccClients#hybrid-client) and [Authorization Code Clients](xref:ccClients#authorization-code-client). Therefore, at least one user should already be added to a tenant when the OCS Portal is first accessed.

You must have the Tenant Administrator role to add and manage users in a tenant.

## <a name="users-pi-server"></a>PI Server counterpart

An OCS user is comparable to a mapping in PI Data Archive. For example, in PI Data Archive a mapping may be added from a Microsoft Windows account to a specified PI identity. The user uses their Windows credentials to authenticate against PI Data Archive and gets the permissions specified by the PI identity. In OCS, a user uses Azure Active Directory, Microsoft accounts, or Google credentials to authenticate against OCS, and users get their permissions from the roles that are assigned to them.

## <a name="users-bp"></a>Users best practices

The following best practices are recommended when you are setting up your users:

- The OCS invitation is sent to the user at the email address specified in the Contact Email field. Therefore, verify that it is correct to ensure that your users receive the invitation and ensure that it is not sent to an unintended recipient, giving them access to OCS.

- Before inviting users to OCS, ensure that they have been granted the correct permissions through their roles. In particular, consider the access granted to the Tenant Member role which, by default, grants read access to everything in the tenant. If a user should not have read access to some resources, the Tenant Member role can be limited.

  