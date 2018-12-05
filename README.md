# Description

ABAP projects that are using ODATA services, and want a basic testing tool for those services, can use smoke-test to verify basic ODATA functionality.    

This ABAP Report performs simple [smoke tests](https://en.wikipedia.org/wiki/Smoke_testing_%28software%29) for activated ODATA services all at once, providing basic automated testing for your ODATA endpoints. These smoke tests mainly cover the retrieval of ODATA service metadata and optionally can perform an arbitary entityset request. The resulting HTTP response codes are collected (e.g. OK = HTTP 200) and displayed in a list view.  

Report Flow:
* Evaluates all activated ODATA Services (as in transaction /IWFND/MAINT_SERVICE)
* Performs a $metadata call
* (Optional) Performs a service document call
* (Optional) Performs an arbitary entityset call
* Collects HTTP Status Codes / Responses and outputs it to the Application Log (transaction SLG1)

# Limitations

There is no validation of request content, data correctness or completeness. Also notice, that for arbitary entityset calls, not necessarily every call might succeed, as some entities require mandatory parameters! Further testing therefore could be done using third party tools, that can verify and correlate each ODATA service request. 

# Requirements

The provided coding works in any environment, that meets the following technical prerequisites:

* **SAP Netweaver ABAP >= 7.51** environment e.g. [SAP S/4HANA](https://blogs.sap.com/?p=745947) - tested only with production copy.
* Software component SAP_GWFND [(Gateway)](https://launchpad.support.sap.com/#/notes/2512479) installed
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

This project is provided "as-is", with no support or changes planned.

# License

Copyright (c) 2018 SAP SE or an SAP affiliate company. All rights reserved.

The content of this repository is licensed under the SAP SAMPLE CODE LICENSE AGREEMENT as noted in the [LICENSE](https://github.com/SAP/abap-odata-smoke-test/blob/master/LICENSE) file.
