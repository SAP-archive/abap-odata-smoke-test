# Purpose

ABAP Report to run simple ODATA smoke tests
* Evaluates all activated ODATA Services
* Performs a $metadata call
* (Optional) Performs a service document call
* (Optional) Performs an arbitary entityset call
* Collects HTTP Status Codes / Response via SAP Application log

![demo smoke test](http://sap.frumania.com/smoke_test.png =500px)

# System Requirements

* tested on NW ABAP >= 7.52
* Requires working GW Client functionality (uses HTTP) - check also transaction "/IWFND/GW_CLIENT"
* User with SAP_ALL or similar authorizations to execute ODATA services and perform entityset calls

# Deployment

* Run transaction "SE38"
* create new executable report e.g. Z_ODATA_SMOKE_TEST
* [Copy & Paste Source Code](https://github.com/SAP/abap-odata-smoke-test/blob/master/Z_ODATA_SMOKE_TEST.txt)
* Save & Activate

# Execution

After deployment, run report via "SE38".

Output/Progress can be observed via transaction "SLG1", Object "/IWFND/", Subobject "RUNTIME".

Flag <test_entity = abap_true.> determines, whether entityset calls are performed (default = on).

> ATTENTION: Depending on the amount of active services, especially the initial execution might take a while!

# License

[SAP Sample Code License Agreement v1.0](https://github.com/SAP/abap-odata-smoke-test/blob/master/SAP%20Sample%20Code%20License%20Agreement%20v1.0.docx)
