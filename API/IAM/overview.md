# IAM API


## 简介
IAM相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addPermissionsToSubUser**|POST|为子用户绑定策略|
|**addSubUserToGroup**|POST|添加子用户到用户组中|
|**attachGroupPolicy**|POST|为用户组绑定策略|
|**attachRolePolicy**|POST|为角色绑定策略|
|**attachSubUserPolicy**|POST|为子用户绑定策略|
|**createGroup**|POST|创建用户组|
|**createPermission**|POST|创建策略|
|**createPolicy**|POST|创建策略|
|**createRole**|POST|创建角色|
|**createSubUser**|POST|创建子用户|
|**createUserAccessKey**|POST|创建主账号AccessKey|
|**deleteGroup**|DELETE|删除用户组|
|**deletePolicy**|DELETE|删除策略|
|**deleteRole**|DELETE|删除角色|
|**deleteSubUser**|DELETE|删除子用户信息|
|**deleteSubUserAccessKey**|DELETE|删除子用户的AccessKey|
|**deleteUserAccessKey**|DELETE|删除AccessKey|
|**describeGroup**|GET|查询用户组详情|
|**describePermissionDetail**|GET|查询策略详情|
|**describePermissions**|GET|查询策略列表|
|**describePolicy**|GET|查询策略详情|
|**describeRole**|GET|查询角色详情|
|**describeSubUser**|GET|查询子用户信息|
|**describeSubUserPermissions**|GET|查询子用户策略列表|
|**describeUserAccessKeys**|GET|查询主账号AccessKey列表|
|**detachGroupPolicy**|DELETE|为用户组解绑策略|
|**detachRolePolicy**|DELETE|为角色绑定策略|
|**detachSubUserPolicy**|DELETE|为子用户解绑策略|
|**disableSubUserAccessKey**|PUT|禁用子用户的AccessKey|
|**disabledUserAccessKey**|PUT|禁用主账号AccessKey|
|**enableSubUserAccessKey**|PUT|启用子用户AccessKey|
|**enabledUserAccessKey**|PUT|启用主账号AccessKey|
|**removePermissionOfSubUser**|DELETE|为子用户解绑策略|
|**removeSubUserFromGroup**|DELETE|将子用户从组中删除|
|**updateAssumeRolePolicy**|PUT|修改角色内置policy|
|**updateGroup**|PUT|修改用户组|
|**updatePermission**|PUT|修改策略|
|**updatePolicyDescription**|PUT|修改策略描述|
|**updateSubUser**|PUT|修改子用户信息|
