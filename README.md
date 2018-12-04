# Description

ODATA services nowadays serve as a foundation of SAP Fiori apps and are therefore utilized at large scale. To ensure that services are working correctly after activation, this ABAP Report can provide simple ODATA smoke testing capabilities for all activated services all at once.

Flow:
* Evaluates all activated ODATA Services (as in transaction /IWFND/MAINT_SERVICE)
* Performs a $metadata call
* (Optional) Performs a service document call
* (Optional) Performs an arbitary entityset call
* Collects HTTP Status Codes / Responses and outputs it to the Application Log (transaction SLG1)

# Requirements

* any **SAP Netweaver ABAP >= 7.51** e.g. [SAP S/4HANA](https://blogs.sap.com/?p=745947)
* Requires software component SAP_GWFND [(Gateway)](https://launchpad.support.sap.com/#/notes/2512479) installed
* Requires working [Gateway Client](https://wiki.scn.sap.com/wiki/display/ABAPConn/Gateway+Client) functionality (uses HTTP) - check also transaction "/IWFND/GW_CLIENT"
* User with SAP_ALL or similar authorizations to execute ODATA services and perform entityset calls

# Download & Installation

It is actually not necessary to download any files, you can easily copy and paste the required code fragments directly, as mentioned below. If you still like to have a local copy, you can follow this [guide](https://help.github.com/articles/cloning-a-repository/).

* Run SAPGUI, execute transaction "SE38"
* create new executable report e.g. Z_ODATA_SMOKE_TEST
* [Copy & Paste Source Code](https://github.com/SAP/abap-odata-smoke-test/blob/master/src/Z_ODATA_SMOKE_TEST.txt)
* Save & Activate

# Execution

After installation/deployment, run report via "SE38".

Flag <test_entity = abap_false.> determines, whether entityset calls are performed (default = off).

> ATTENTION: Depending on the amount of active services, especially the initial execution can take minutes up to couple of hours!

### Output

Once finished, results will be shown automatically! Moreover, they can also be observed via transaction "SLG1", Object "/IWFND/", Subobject "RUNTIME", as seen below. The result list can easily be sorted and help during further troubleshooting.

![demo smoke test](https://github.com/SAP/abap-odata-smoke-test/blob/master/docs/img/smoke_test.png)

# Support

This project is provided "as-is": there is no guarantee that raised issues will be answered or addressed.

# License

Copyright (c) 2018 SAP SE or an SAP affiliate company. All rights reserved.

The content of this repository is licensed under the SAP SAMPLE CODE LICENSE AGREEMENT as noted in the [LICENSE](https://github.com/SAP/abap-odata-smoke-test/blob/master/LICENSE) file.
