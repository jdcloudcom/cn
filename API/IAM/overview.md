# IAM API


## 简介
IAM相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addPermissionsToSubUser**|POST|为子用户绑定策略|
|**addSubUserToGroup**|POST|添加子账号到用户组中|
|**attachGroupPolicy**|POST|为用户组绑定策略|
|**attachRolePolicy**|POST|为角色绑定策略|
|**attachSubUserPolicy**|POST|为子用户绑定策略|
|**createGroup**|POST|创建用户组|
|**createPermission**|POST|创建策略|
|**createPolicy**|POST|创建策略|
|**createRole**|POST|创建角色|
|**createSubUser**|POST|创建子账号|
|**createSubuser**|POST|创建子账号|
|**createUserAccessKey**|POST|创建AccessKey|
|**deleteGroup**|DELETE|删除用户组|
|**deletePolicy**|DELETE|删除策略|
|**deleteRole**|DELETE|删除角色|
|**deleteSubUser**|DELETE|删除子账号信息|
|**deleteUserAccessKey**|DELETE|删除AccessKey|
|**describeAttachedUserPolicies**|GET|列举用户组的策略|
|**describeGroup**|GET|查询用户组详情|
|**describeGroups**|GET|查询用户组列表|
|**describePermissionDetail**|GET|查询策略详情|
|**describePermissions**|GET|查询策略列表|
|**describePolicies**|GET|查询策略列表|
|**describePolicy**|GET|查询策略详情|
|**describeRole**|GET|查询角色详情|
|**describeRolePolicies**|GET|查询角色授权策略列表|
|**describeRoles**|GET|查询角色列表|
|**describeSubUser**|GET|查询子账号信息|
|**describeSubUserGroups**|GET|查询子账号所属的所有组|
|**describeSubUserPermissions**|GET|查询子用户策略列表|
|**describeSubUserPolicies**|GET|查询子用户策略列表|
|**describeSubUsers**|GET|查询子账号列表|
|**describeUserAccessKeys**|GET|查询AccessKey列表|
|**detachGroupPolicy**|DELETE|为用户组解绑策略|
|**detachRolePolicy**|DELETE|为角色绑定策略|
|**detachSubUserPolicy**|DELETE|为子用户解绑策略|
|**disabledUserAccessKey**|PUT|禁用AccessKey|
|**enabledUserAccessKey**|PUT|启用AccessKey|
|**removePermissionOfSubUser**|DELETE|为子用户解绑策略|
|**removeSubUserFromGroup**|DELETE|将子账号从组中删除|
|**updateAssumeRolePolicy**|PUT|修改角色内置policy|
|**updateGroup**|PUT|修改用户组|
|**updatePermission**|PUT|修改策略|
|**updatePolicy**|PUT|修改策略|
|**updateRole**|PUT|修改角色基本信息|
|**updateSubUser**|PUT|修改子账号信息|
