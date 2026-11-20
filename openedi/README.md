# OpenEDI templates

Each file is the OpenEDI template of one transaction: an OpenAPI 3 document whose `components/schemas` describe the transaction, its loops, segments, composites, data elements and codes. The schema names are the JSON property names that ediFabric Cloud, .NET and Native read and write.

Use a template to:

- generate classes for the transaction in your language (see [Generate classes from a template](../README.md#generate-classes-from-an-openedi-template));
- start a custom model for a trading partner in the [EDI Spec Builder](https://www.edifabric.com/spec-builder/index.html);
- read the transaction's structure. The spec library page next to each template shows the same model as a guide.

The [EDI spec library](https://www.edifabric.com/specs/index.html) has a model for every transaction in every supported version. These templates are copies of the ones it publishes, and the library is the source when they differ.

## X12 HIPAA 5010

| Transaction | Name | Version | Template | Spec |
|---|---|---|---|---|
| 270 | Eligibility, Coverage or Benefit Inquiry | 005010X279A1 | [en-270-openedi.json](x12/hipaa/005010/270/en-270-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/270.html) |
| 271 | Eligibility, Coverage or Benefit Information | 005010X279A1 | [en-271-openedi.json](x12/hipaa/005010/271/en-271-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/271.html) |
| 276 | Health Care Claim Status Request | 005010X212 | [en-276-openedi.json](x12/hipaa/005010/276/en-276-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/276.html) |
| 277 | Health Care Claim Status Response | 005010X212 | [en-277-openedi.json](x12/hipaa/005010/277/en-277-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/277.html) |
| 278 | Health Care Services Review: Request for Review and Response | 005010X217 | [en-278-openedi.json](x12/hipaa/005010/278/en-278-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/278.html) |
| 820 | Payroll Deducted and Other Group Premium Payment for Insurance Products | 005010X218 | [en-820-openedi.json](x12/hipaa/005010/820/en-820-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/820.html) |
| 820HIX | Health Insurance Exchange Related Payments | 005010X306 | [en-820HIX-openedi.json](x12/hipaa/005010/820hix/en-820HIX-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/820hix.html) |
| 834 | Benefit Enrollment and Maintenance | 005010X220A1 | [en-834-openedi.json](x12/hipaa/005010/834/en-834-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/834.html) |
| 835 | Health Care Claim Payment/Advice | 005010X221A1 | [en-835-openedi.json](x12/hipaa/005010/835/en-835-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/835.html) |
| 837D | Health Care Claim: Dental | 005010X224A2 | [en-837D-openedi.json](x12/hipaa/005010/837d/en-837D-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/837d.html) |
| 837I | Health Care Claim: Institutional | 005010X223A2 | [en-837I-openedi.json](x12/hipaa/005010/837i/en-837I-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/837i.html) |
| 837P | Health Care Claim: Professional | 005010X222A1 | [en-837P-openedi.json](x12/hipaa/005010/837p/en-837P-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/hipaa/005010/837p.html) |

## X12

| Transaction | Name | Version | Template | Spec |
|---|---|---|---|---|
| 210 | Motor Carrier Freight Details and Invoice | 004010 | [en-210-openedi.json](x12/004010/210/en-210-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/210.html) |
| 214 | Transportation Carrier Shipment Status Message | 004010 | [en-214-openedi.json](x12/004010/214/en-214-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/214.html) |
| 404 | Rail Carrier Shipment Information | 004010 | [en-404-openedi.json](x12/004010/404/en-404-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/404.html) |
| 810 | Invoice | 004010 | [en-810-openedi.json](x12/004010/810/en-810-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/810.html) |
| 824 | Application Advice | 004010 | [en-824-openedi.json](x12/004010/824/en-824-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/824.html) |
| 832 | Price/Sales Catalog | 004010 | [en-832-openedi.json](x12/004010/832/en-832-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/832.html) |
| 850 | Purchase Order | 004010 | [en-850-openedi.json](x12/004010/850/en-850-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/850.html) |
| 855 | Purchase Order Acknowledgment | 004010 | [en-855-openedi.json](x12/004010/855/en-855-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/855.html) |
| 856 | Ship Notice/Manifest | 004010 | [en-856-openedi.json](x12/004010/856/en-856-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/856.html) |
| 857 | Shipment and Billing Notice | 004010 | [en-857-openedi.json](x12/004010/857/en-857-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/857.html) |
| 861 | Receiving Advice/Acceptance Certificate | 004010 | [en-861-openedi.json](x12/004010/861/en-861-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/861.html) |
| 894 | Delivery/Return Base Record | 004010 | [en-894-openedi.json](x12/004010/894/en-894-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/894.html) |
| 945 | Warehouse Shipping Advice | 004010 | [en-945-openedi.json](x12/004010/945/en-945-openedi.json) | [Spec](https://www.edifabric.com/specs/x12/004010/945.html) |

## EDIFACT and EANCOM

| Transaction | Name | Version | Template | Spec |
|---|---|---|---|---|
| EANCOM INVOIC | Invoice message | D01B | [en-INVOIC-openedi.json](eancom/d01b-syntax-3/invoic/en-INVOIC-openedi.json) | [Spec](https://www.edifabric.com/specs/eancom/d01b-syntax-3/invoic.html) |
| CUSCAR | Customs cargo report message | D03B | [en-CUSCAR-openedi.json](edifact/d03b/cuscar/en-CUSCAR-openedi.json) | [Spec](https://www.edifabric.com/specs/edifact/d03b/cuscar.html) |
| PAXLST | Passenger list message | D03B | [en-PAXLST-openedi.json](edifact/d03b/paxlst/en-PAXLST-openedi.json) | [Spec](https://www.edifabric.com/specs/edifact/d03b/paxlst.html) |
| DESADV | Despatch advice message | D96A | [en-DESADV-openedi.json](edifact/d96a/desadv/en-DESADV-openedi.json) | [Spec](https://www.edifabric.com/specs/edifact/d96a/desadv.html) |
| IFTMIN | Instruction message | D96A | [en-IFTMIN-openedi.json](edifact/d96a/iftmin/en-IFTMIN-openedi.json) | [Spec](https://www.edifabric.com/specs/edifact/d96a/iftmin.html) |
| IFTSTA | International multimodal status report message | D96A | [en-IFTSTA-openedi.json](edifact/d96a/iftsta/en-IFTSTA-openedi.json) | [Spec](https://www.edifabric.com/specs/edifact/d96a/iftsta.html) |
| INVOIC | Invoice message | D96A | [en-INVOIC-openedi.json](edifact/d96a/invoic/en-INVOIC-openedi.json) | [Spec](https://www.edifabric.com/specs/edifact/d96a/invoic.html) |
| ORDERS | Purchase order message | D96A | [en-ORDERS-openedi.json](edifact/d96a/orders/en-ORDERS-openedi.json) | [Spec](https://www.edifabric.com/specs/edifact/d96a/orders.html) |
| ORDRSP | Purchase order response message | D96A | [en-ORDRSP-openedi.json](edifact/d96a/ordrsp/en-ORDRSP-openedi.json) | [Spec](https://www.edifabric.com/specs/edifact/d96a/ordrsp.html) |
| PRICAT | Price/sales catalogue message | D96A | [en-PRICAT-openedi.json](edifact/d96a/pricat/en-PRICAT-openedi.json) | [Spec](https://www.edifabric.com/specs/edifact/d96a/pricat.html) |

## HL7

| Transaction | Name | Version | Template | Spec |
|---|---|---|---|---|
| MDMT02 | Original document notification and content | 2.6 | [en-MDMT02-openedi.json](hl7/2.6/mdmt02/en-MDMT02-openedi.json) | [Spec](https://www.edifabric.com/specs/hl7/2.6/mdmt02.html) |
| ORUR01 | Unsolicited transmission of an observation message | 2.6 | [en-ORUR01-openedi.json](hl7/2.6/orur01/en-ORUR01-openedi.json) | [Spec](https://www.edifabric.com/specs/hl7/2.6/orur01.html) |
| QBPZ81 | Query by parameter Z81 | 2.6 | [en-QBPZ81-openedi.json](hl7/2.6/qbpz81/en-QBPZ81-openedi.json) | [Spec](https://www.edifabric.com/specs/hl7/2.6/qbpz81.html) |
| RDSO13 | Pharmacy/treatment dispense | 2.6 | [en-RDSO13-openedi.json](hl7/2.6/rdso13/en-RDSO13-openedi.json) | [Spec](https://www.edifabric.com/specs/hl7/2.6/rdso13.html) |

## NCPDP

| Transaction | Name | Version | Template | Spec |
|---|---|---|---|---|
| CHGRES | Prescription Change Response | 10.6 | [en-CHGRES-openedi.json](ncpdp/script-10.6/chgres/en-CHGRES-openedi.json) | [Spec](https://www.edifabric.com/specs/ncpdp/script-10.6/chgres.html) |
| NEWRX | New Prescription Request | 10.6 | [en-NEWRX-openedi.json](ncpdp/script-10.6/newrx/en-NEWRX-openedi.json) | [Spec](https://www.edifabric.com/specs/ncpdp/script-10.6/newrx.html) |
| REFREQ | Refill Request | 10.6 | [en-REFREQ-openedi.json](ncpdp/script-10.6/refreq/en-REFREQ-openedi.json) | [Spec](https://www.edifabric.com/specs/ncpdp/script-10.6/refreq.html) |
| B1 | Billing Request | D.0 | [en-B1-openedi.json](ncpdp/telecommunication-d0/b1/en-B1-openedi.json) | [Spec](https://www.edifabric.com/specs/ncpdp/telecommunication-d0/b1.html) |
| RESPONSE | Telecommunication response | D.0 | [en-RESPONSE-openedi.json](ncpdp/telecommunication-d0/response/en-RESPONSE-openedi.json) | [Spec](https://www.edifabric.com/specs/ncpdp/telecommunication-d0/response.html) |

## VDA

| Transaction | Name | Version | Template | Spec |
|---|---|---|---|---|
| 4905 | Delivery instruction | VDA | [en-4905-openedi.json](vda/4905/en-4905-openedi.json) | [Spec](https://www.edifabric.com/specs/vda/4905.html) |

## EDIG@S

| Transaction | Name | Version | Template | Spec |
|---|---|---|---|---|
| NOMINT | Nomination Message | 4.0 | [en-NOMINT-openedi.json](edigas/4.0/nomint/en-NOMINT-openedi.json) | [Spec](https://www.edifabric.com/specs/edigas/4.0/nomint.html) |

## IATA

| Transaction | Name | Version | Template | Spec |
|---|---|---|---|---|
| PNRGOV | Passenger name record data for governments | 13.1 | [en-PNRGOV-openedi.json](iata/13.1/pnrgov/en-PNRGOV-openedi.json) | [Spec](https://www.edifabric.com/specs/iata/13.1/pnrgov.html) |
