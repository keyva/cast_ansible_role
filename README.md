# Ansible Role for CAST Highlight Software

This project shares an Ansible Role developed for the consumption of CAST Highlight Software API. By using this role, Ansible users can automatically trigger an application assessment for various technologies supported by CAST.  

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. 

1) Clone the repository, or download the role files on to your Ansible instance
2) Review the demo_cast_role.yaml file, which demonstrates how to use the keyva_cast role. The explanation of various name value pairs that can be listed are explained in the "Role Arguments" section.

### Prerequisites

1) You will need a working JRE environment for this role to work installed on the target system on which this role is run. Java 8 or above is supported by the CAST API.

```
[root@castdemo ~]# java -version
openjdk version "1.8.0_212"
OpenJDK Runtime Environment (build 1.8.0_212-b04)
OpenJDK 64-Bit Server VM (build 25.212-b04, mixed mode)
```

2) You will need the application source code on that target system you run the role on. The Ansible role will evaluate the characteristics of the source code (without extracting any of the code), and visually show the metrics on the CAST portal.


### Installing

To install the Ansible role, copy the roles directory in the same folder from where the playbook calling the role is set up. You can take all the files as is (within this Github project) and place them all under the same folder, and then call the demo_cast_role.yaml file.

Once all the files are copied, the sample playbook calling the developed role looks like the below. Replace the given values with relevant values for your environment. If you'd like a free assessment of your application, you can skip the upload, and send the exported files to Keyva for a visual assessment on the CAST portal. No source code is ever exported during the assessment, only the application characteristics are captured.

```
---
- name: "Run Keyva CAST"
  hosts: all 
  roles:
  - role: keyva_cast
    vars:
      keyva_cast_source_dir: "/root/samples/sample-code-java/src/"
      keyva_cast_working_dir: "/root/samples/Highlight-Automation-Command"
      keyva_cast_skip_upload: true
```

If you have access to the CAST portal, you can export the assessment results directly your CAST instance. 

```
---
- name: "Run Keyva CAST"
  hosts: all 
  roles:
  - role: keyva_cast
    vars:
      keyva_cast_source_dir: "/root/samples/sample-code-java/src/"
      keyva_cast_working_dir: "/root/samples/Highlight-Automation-Command"
      keyva_cast_skip_upload: false 
      keyva_cast_login: "user@email.com"
      keyva_cast_password: "Password"
      keyva_cast_server_url: "https://rpa.casthighlight.com"
      keyva_cast_application_id: 33412
      keyva_cast_company_id: 7154
```


The CAST portal captures and visually displays characteristics like Software Agility, Business Impact, Cloud Readiness, and more.




## Role Arguments

Add additional notes about how to deploy this on a live system


## Versioning

Initial Release. v1.0.

## Authors

* **Keyva** - *Initial work* - [Keyva](www.keyvatech.com)

For any questions about pull requests, or other questions related to this work, please email info@keyvatech.com

## License

This code is distributed under GNU General Public License.
Copyright (C) 2019 www.keyvatech.com

```
This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```

If you have questions or need assistance, please reach out to info@keyvatech.com

