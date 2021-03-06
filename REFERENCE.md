# Reference
<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

**Classes**

_Public Classes_

* [`openondemand`](#openondemand): Manage Open OnDemand

_Private Classes_

* `openondemand::apache`: Manage Open OnDemand Apache
* `openondemand::config`: Manage Open OnDemand configs
* `openondemand::install`: Manage Open OnDemand install
* `openondemand::repo`: Manage Open OnDemand repos
* `openondemand::service`: Manage Open OnDemand service

**Defined types**

* [`openondemand::app::dev`](#openondemandappdev): Manage Open OnDemand dev app
* [`openondemand::app::usr`](#openondemandappusr): Manage Open OnDemand user app
* [`openondemand::cluster`](#openondemandcluster): Manage Open OnDemand cluster definition
* [`openondemand::install::app`](#openondemandinstallapp): Manage Open OnDemand app

**Data types**

* [`Openondemand::Acl`](#openondemandacl): OnDemand cluster ACL
* [`Openondemand::Batch_connect`](#openondemandbatch_connect): Defines cluster config batch_connect values
* [`Openondemand::Nginx_stage_namespace_config`](#openondemandnginx_stage_namespace_config): nginx_stage.yml namespace_config

**Tasks**

* [`maintenance`](#maintenance): Put OnDemand into maintenance mode

## Classes

### openondemand

Manage Open OnDemand

#### Parameters

The following parameters are available in the `openondemand` class.

##### `repo_release`

Data type: `String`

The release of OnDemand repo

Default value: 'latest'

##### `repo_baseurl_prefix`

Data type: `Variant[Stdlib::HTTPSUrl, Stdlib::HTTPUrl]`

The baseurl prefix for OnDemand repo

Default value: 'https://yum.osc.edu/ondemand'

##### `repo_gpgkey`

Data type: `Variant[Stdlib::HTTPSUrl, Stdlib::HTTPUrl, Stdlib::Absolutepath]`

The URL for OnDemand repo GPG key

Default value: 'https://yum.osc.edu/ondemand/RPM-GPG-KEY-ondemand'

##### `manage_scl`

Data type: `Boolean`

Boolean that determines if managing SCL

Default value: `true`

##### `selinux`

Data type: `Boolean`

Boolean that determines if adding SELinux support

Default value: `false`

##### `ondemand_package_ensure`

Data type: `String`

ondemand package ensure

Default value: 'present'

##### `mod_auth_openidc_ensure`

Data type: `String`

mod_auth_openidc package ensure

Default value: 'present'

##### `install_apps`

Data type: `Hash`

Hash of apps to install, passed to ondemand::install::app

Default value: {}

##### `declare_apache`

Data type: `Boolean`

Boolean that determines if apache is declared or included

Default value: `true`

##### `apache_scls`

Data type: `String`

SCLs to load when starting Apache service

Default value: 'httpd24 rh-ruby25'

##### `cilogon_client_id`

Data type: `String`

CILogon client_id

Default value: ''

##### `cilogon_client_secret`

Data type: `String`

CILogon client_secret

Default value: ''

##### `oidc_crypto_passphrase`

Data type: `String`

OIDC crypto passphrase

Default value: 'CHANGEME'

##### `listen_addr_port`

Data type: `Variant[Array, String, Undef]`

ood_portal.yml listen_addr_port

Default value: `undef`

##### `servername`

Data type: `Optional[String]`

ood_portal.yml servername

Default value: `undef`

##### `ssl`

Data type: `Optional[Array]`

ood_portal.yml ssl

Default value: `undef`

##### `logroot`

Data type: `String`

ood_portal.yml logroot

Default value: 'logs'

##### `use_rewrites`

Data type: `Boolean`

ood_portal.yml use_rewrites

Default value: `true`

##### `use_maintenance`

Data type: `Boolean`

ood_portal.yml use_maintenance

Default value: `true`

##### `maintenance_ip_whitelist`

Data type: `Array`

ood_portal.yml maintenance_ip_whitelist

Default value: []

##### `maintenance_source`

Data type: `Optional[String]`

Source for maintenance index.html

Default value: `undef`

##### `maintenance_content`

Data type: `Optional[String]`

Content for maintenance index.html

Default value: `undef`

##### `lua_root`

Data type: `String`

ood_portal.yml lua_root

Default value: '/opt/ood/mod_ood_proxy/lib'

##### `lua_log_level`

Data type: `Optional[String]`

ood_portal.yml lua_log_level

Default value: `undef`

##### `user_map_cmd`

Data type: `String`

ood_portal.yml user_map_cmd

Default value: '/opt/ood/ood_auth_map/bin/ood_auth_map.regex'

##### `user_env`

Data type: `Optional[String]`

ood_portal.yml user_env

Default value: `undef`

##### `map_fail_uri`

Data type: `Optional[String]`

ood_portal.yml map_fail_uri

Default value: `undef`

##### `auth_type`

Data type: `Enum['CAS', 'openid-connect', 'shibboleth', 'ldap', 'basic']`

ood_portal.yml auth_type

Default value: 'basic'

##### `auth_configs`

Data type: `Optional[Array]`

ood_portal.yml auth_configs

Default value: `undef`

##### `root_uri`

Data type: `String`

ood_portal.yml root_uri

Default value: '/pun/sys/dashboard'

##### `analytics`

Data type: `Optional[Struct[{url => String, id => String}]]`

ood_portal.yml analytics

Default value: `undef`

##### `public_uri`

Data type: `String`

ood_portal.yml public_uri

Default value: '/public'

##### `public_root`

Data type: `String`

ood_portal.yml public_root

Default value: '/var/www/ood/public'

##### `logout_uri`

Data type: `String`

ood_portal.yml logout_uri

Default value: '/logout'

##### `logout_redirect`

Data type: `String`

ood_portal.yml logout_redirect

Default value: '/pun/sys/dashboard/logout'

##### `host_regex`

Data type: `String`

ood_portal.yml host_regex

Default value: '[^/]+'

##### `node_uri`

Data type: `Optional[String]`

ood_portal.yml node_uri

Default value: `undef`

##### `rnode_uri`

Data type: `Optional[String]`

ood_portal.yml rnode_uri

Default value: `undef`

##### `nginx_uri`

Data type: `String`

ood_portal.yml nginx_uri

Default value: '/nginx'

##### `pun_uri`

Data type: `String`

ood_portal.yml pun_uri

Default value: '/pun'

##### `pun_socket_root`

Data type: `String`

ood_portal.yml pun_socket_root

Default value: '/var/run/ondemand-nginx'

##### `pun_max_retries`

Data type: `Integer`

ood_portal.yml pun_max_retries

Default value: 5

##### `oidc_uri`

Data type: `Optional[String]`

ood_portal.yml oidc_uri

Default value: `undef`

##### `oidc_discover_uri`

Data type: `Optional[String]`

ood_portal.yml oidc_discover_uri

Default value: `undef`

##### `oidc_discover_root`

Data type: `Optional[String]`

ood_portal.yml oidc_discover_root

Default value: `undef`

##### `register_uri`

Data type: `Optional[String]`

ood_portal.yml register_uri

Default value: `undef`

##### `register_root`

Data type: `Optional[String]`

ood_portal.yml register_root

Default value: `undef`

##### `oidc_provider`

Data type: `Optional[String]`

OIDC provider

Default value: `undef`

##### `oidc_provider_token_endpoint_auth`

Data type: `Optional[String]`

OIDC provider token_endpoint_auth

Default value: `undef`

##### `oidc_provider_scope`

Data type: `String`

OIDC provider scope

Default value: 'openid email'

##### `oidc_provider_client_id`

Data type: `String`

OIDC provider client_id

Default value: ''

##### `oidc_provider_client_secret`

Data type: `String`

OIDC provider client_secret

Default value: ''

##### `oidc_session_inactivity_timeout`

Data type: `Integer`

mod_auth_openidc OIDCSessionInactivityTimeout

Default value: 28800

##### `oidc_session_max_duration`

Data type: `Integer`

mod_auth_openidc OIDCSessionMaxDuration

Default value: 28800

##### `oidc_remote_user_claim`

Data type: `Optional[String]`

OIDC provider remote_user claim

Default value: `undef`

##### `oidc_pass_claims_as`

Data type: `String`

mod_auth_openidc OIDCPassClaimsAs

Default value: 'environment'

##### `oidc_extra_configs`

Data type: `Hash`

OIDC extra settings for mod_auth_openidc

Default value: {}

##### `web_directory`

Data type: `Stdlib::Absolutepath`

Path to main web directory for OnDemand

Default value: '/var/www/ood'

##### `basic_auth_users`

Data type: `Hash`

Hash of resources to pass to httpauth for defining basic auth users
Only used with basic auth

Default value: {}

##### `nginx_log_group`

Data type: `String`

Group to set for /var/log/ondemand-nginx

Default value: 'ondemand-nginx'

##### `nginx_stage_ondemand_portal`

Data type: `String`

nginx_stage.yml ondemand_portal

Default value: 'ondemand'

##### `nginx_stage_ondemand_title`

Data type: `String`

nginx_stage.yml ondemand_title

Default value: 'Open OnDemand'

##### `nginx_stage_pun_custom_env`

Data type: `Hash`

nginx_stage.yml pun_custom_env

Default value: {}

##### `nginx_stage_app_root`

Data type: `Openondemand::Nginx_stage_namespace_config`

nginx_stage.yml app_root

Default value: {}

##### `nginx_stage_scl_env`

Data type: `String`

nginx_stage.yml scl_env

Default value: 'ondemand'

##### `nginx_stage_app_request_regex`

Data type: `Optional[Openondemand::Nginx_stage_namespace_config]`

nginx_stage.yml app_request_regex

Default value: `undef`

##### `clusters`

Data type: `Hash`

Hash of resources to apss to openondemand::cluster

Default value: {}

##### `clusters_hiera_merge`

Data type: `Boolean`

Boolean that determines if clusters should be merged via lookup function

Default value: `true`

##### `usr_apps`

Data type: `Variant[Array, Hash]`

Resources passed to openondemand::app::usr

Default value: {}

##### `usr_app_defaults`

Data type: `Hash`

Defaults for `usr_apps` resources

Default value: {}

##### `dev_apps`

Data type: `Hash`

Resources passed to openondemand::app::dev

Default value: {}

##### `dev_app_users`

Data type: `Array`

Users to define as having dev apps, passed to openondemand::app::dev

Default value: []

##### `dev_app_defaults`

Data type: `Hash`

Defaults for `dev_apps` and `dev_app_users`

Default value: {}

##### `apps_config_repo`

Data type: `Optional[String]`

Git repo URL for apps config

Default value: `undef`

##### `apps_config_revision`

Data type: `Optional[String]`

Revision for apps config Git repo

Default value: `undef`

##### `apps_config_repo_path`

Data type: `String`

Path in apps config Git repo for app configs

Default value: ''

##### `locales_config_repo_path`

Data type: `Optional[String]`

Path in apps config Git repo for locales configs

Default value: `undef`

##### `announcements_config_repo_path`

Data type: `Optional[String]`

Path in apps config Git repo for announcements

Default value: `undef`

##### `apps_config_source`

Data type: `Optional[String]`

Source for apps config, not used if `apps_config_repo` is defined

Default value: `undef`

##### `locales_config_source`

Data type: `Optional[String]`

Source for locales config, not used if `apps_config_repo` is defined

Default value: `undef`

##### `announcements_config_source`

Data type: `Optional[String]`

Source for aouncements config, not used if `apps_config_repo` is defined

Default value: `undef`

##### `public_files_repo_paths`

Data type: `Array`

Path to public files in apps config Git repo

Default value: []

##### `manage_logrotate`

Data type: `Boolean`

Boolean that allows disabling management of logrotate

Default value: `true`

## Defined types

### openondemand::app::dev

Manage Open OnDemand dev app

#### Examples

##### 

```puppet
openondemand::app::dev { 'user1': }
```

#### Parameters

The following parameters are available in the `openondemand::app::dev` defined type.

##### `ensure`

Data type: `Enum['present','absent']`



Default value: 'present'

##### `mode`

Data type: `Stdlib::Filemode`

File mode of dev app

Default value: '0755'

##### `owner`

Data type: `String`

Owner of dev app

Default value: 'root'

##### `group`

Data type: `String`

Group owning dev app

Default value: 'root'

##### `home_subdir`

Data type: `String`

The subdirectory under user's home for dev app
Not used if `gateway_src` is defined

Default value: 'ondemand/dev'

##### `gateway_src`

Data type: `Optional[Stdlib::Absolutepath]`

The path to dev app, overrides `home_subdir`

Default value: `undef`

### openondemand::app::usr

Manage Open OnDemand user app

#### Examples

##### 

```puppet
openondemand::app::usr { 'user1':
  gateway_src => '/home/user1/ondemand/usr',
}
```

#### Parameters

The following parameters are available in the `openondemand::app::usr` defined type.

##### `gateway_src`

Data type: `Stdlib::Absolutepath`

Path to source of user's apps

##### `ensure`

Data type: `Enum['present','absent']`



Default value: 'present'

##### `mode`

Data type: `Stdlib::Filemode`

The file mode for shared apps

Default value: '0750'

##### `owner`

Data type: `String`

The file owner of shared apps

Default value: 'root'

##### `group`

Data type: `String`

The file group owner of shared apps

Default value: 'root'

### openondemand::cluster

Manage Open OnDemand cluster definition

#### Parameters

The following parameters are available in the `openondemand::cluster` defined type.

##### `cluster_title`

Data type: `String`



Default value: $name

##### `url`

Data type: `Optional[Variant[Stdlib::HTTPSUrl, Stdlib::HTTPUrl] ]`



Default value: `undef`

##### `hidden`

Data type: `Boolean`



Default value: `false`

##### `acls`

Data type: `Array[Openondemand::Acl]`



Default value: []

##### `login_host`

Data type: `Optional[Stdlib::Host]`



Default value: `undef`

##### `job_adapter`

Data type: `Optional[Enum['torque','slurm','lsf','pbspro','sge']]`



Default value: `undef`

##### `job_cluster`

Data type: `Optional[String]`



Default value: `undef`

##### `job_host`

Data type: `Optional[Stdlib::Host]`



Default value: `undef`

##### `job_lib`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `job_libdir`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `job_bin`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `job_bindir`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `job_conf`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `job_envdir`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `job_serverdir`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `job_exec`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `sge_root`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `libdrmaa_path`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `job_version`

Data type: `Optional[String]`



Default value: `undef`

##### `job_bin_overrides`

Data type: `Hash[String, Stdlib::Absolutepath]`



Default value: {}

##### `scheduler_type`

Data type: `Optional[Enum['moab']]`



Default value: `undef`

##### `scheduler_host`

Data type: `Optional[Stdlib::Host]`



Default value: `undef`

##### `scheduler_bin`

Data type: `Optional[Stdlib::Absolutepath]`



Default value: `undef`

##### `scheduler_version`

Data type: `Optional[String]`



Default value: `undef`

##### `scheduler_params`

Data type: `Hash`



Default value: {}

##### `rsv_query_acls`

Data type: `Array[Openondemand::Acl]`



Default value: []

##### `ganglia_host`

Data type: `Optional[Stdlib::Host]`



Default value: `undef`

##### `ganglia_scheme`

Data type: `String`



Default value: 'https://'

##### `ganglia_segments`

Data type: `Array`



Default value: ['gweb', 'graph.php']

##### `ganglia_req_query`

Data type: `Hash`



Default value: {'c' => $name}

##### `ganglia_opt_query`

Data type: `Hash`



Default value: {'h' => "%{h}.${::domain}"}

##### `ganglia_version`

Data type: `String`



Default value: '3'

##### `grafana_host`

Data type: `Optional[Variant[Stdlib::HTTPSUrl,Stdlib::HTTPUrl]]`



Default value: `undef`

##### `grafana_org_id`

Data type: `Integer`



Default value: 1

##### `grafana_theme`

Data type: `Optional[String]`



Default value: `undef`

##### `grafana_dashboard_name`

Data type: `Optional[String]`



Default value: `undef`

##### `grafana_dashboard_uid`

Data type: `Optional[String]`



Default value: `undef`

##### `grafana_dashboard_panels`

Data type: `Optional[Struct[{
    'cpu' => Integer,
    'memory' => Integer,
  }]]`



Default value: `undef`

##### `grafana_labels`

Data type: `Optional[Struct[{
    'cluster' => String,
    'host' => String,
    'jobid' => Optional[String],
  }]]`



Default value: `undef`

##### `batch_connect`

Data type: `Hash[String, Openondemand::Batch_connect]`



Default value: {}

### openondemand::install::app

Manage Open OnDemand app

#### Examples

##### 

```puppet
openondemand::install::app { 'bc_osc_foo':
  ensure => '0.1.0-1.el7',
}
```

#### Parameters

The following parameters are available in the `openondemand::install::app` defined type.

##### `ensure`

Data type: `String`

Package ensure property if installing from a package

Default value: 'present'

##### `package`

Data type: `String`

Package name for the app

Default value: "ondemand-${name}"

##### `manage_package`

Data type: `Boolean`

Should package be managed

Default value: `true`

##### `path`

Data type: `Optional[Stdlib::Absolutepath]`

Path to app, defaults to `/var/www/ood/apps/sys/$name`

Default value: `undef`

##### `owner`

Data type: `String`

File owner of app

Default value: 'root'

##### `group`

Data type: `String`

File group owner of app

Default value: 'root'

##### `mode`

Data type: `String`

File mode for app

Default value: '0755'

## Data types

### Openondemand::Acl

OnDemand cluster ACL

Alias of `Struct[{ 'adapter' => Enum['group'],
                                  'groups'  => Optional[Array],
                                  'type'    => Enum['whitelist', 'blacklist']
                                  }]`

### Openondemand::Batch_connect

Defines cluster config batch_connect values

Alias of `Struct[{
                                    'script_wrapper' => String,
                                    }]`

### Openondemand::Nginx_stage_namespace_config

nginx_stage.yml namespace_config

Alias of `Struct[{
  'dev' => Optional[String],
  'usr' => Optional[String],
  'sys' => Optional[String]
  }]`

## Tasks

### maintenance

Put OnDemand into maintenance mode

**Supports noop?** false

#### Parameters

##### `ensure`

Data type: `Enum['present','absent']`

Set state of maintenance mode

