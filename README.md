# ediFabric Cloud OpenAPI

OpenAPI 3 definitions of the [ediFabric Cloud](https://www.edifabric.com/docs/edifabric-cloud/introduction.html) REST API, and the OpenEDI templates of the EDI transactions it reads and writes. Use them to generate a client SDK in your language, to import the API into Postman or another API tool, or to generate classes for an EDI transaction.

| Folder | What it has |
|---|---|
| [`v3/openapi.json`](v3/openapi.json) | API v3: Parse and Build for X12 and HIPAA 5010. Parse translates, validates up to SNIP level 4 and acknowledges in one call. |
| [`v2/openapi.json`](v2/openapi.json) | API v2: read, write, validate and acknowledge for X12, HIPAA, EDIFACT, EANCOM, HL7, NCPDP and VDA, and the model operations. |
| [`openedi/`](openedi/README.md) | 47 OpenEDI templates, one per transaction, for X12, HIPAA, EDIFACT, EANCOM, HL7, NCPDP, VDA, EDIG@S and IATA. |

Interactive reference pages: [v3](https://www.edifabric.com/docs/edifabric-cloud/api-v3.html) · [v2](https://www.edifabric.com/docs/edifabric-cloud/api-v2.html)

## Which version

Use **v3** for X12 and HIPAA. One Parse call returns the JSON, the validation report and the 999, 997 or TA1 acknowledgment, and counts as one operation. Use **v2** for every other format. Both are live side by side until v3 supports all formats. The X12 JSON differs between them, so don't mix v2 and v3 calls on the same data: see [API versions](https://www.edifabric.com/docs/edifabric-cloud/introduction.html#api-versions).

## Try it

The demo serial key `bd96a836feca45cb91c86ee65d281f52` works without an account and has a small daily quota. Send it in the `Ocp-Apim-Subscription-Key` header. When it runs out (HTTP 403), [sign up free for Community](https://www.edifabric.com/pricing.html) and use your own serial key. Keep your own key out of source control.

```bash
curl -X POST "https://api.edination.com/v3/x12/parse?mode=3" \
  -H "Ocp-Apim-Subscription-Key: bd96a836feca45cb91c86ee65d281f52" \
  -H "Content-Type: application/octet-stream" \
  -D headers.txt -o response.bin \
  --data-binary @claim.837
```

In modes 2 and 3, the Parse response is the interchange JSON followed by the validation report. Split it at the byte offset in the `X-EdiFabric-Offset` response header. A generated client returns that body as bytes or a file, so split it in your code:

```python
offset = int(headers["X-EdiFabric-Offset"])
interchanges = json.loads(body[:offset])
report = json.loads(body[offset:])
```

## Generate a client SDK

Any OpenAPI 3 generator works. The commands below use [OpenAPI Generator](https://openapi-generator.tech/), which is free and needs Java 11 or later, or Docker. Swap `v3` for `v2` to generate a v2 client.

```bash
npm install -g @openapitools/openapi-generator-cli
openapi-generator-cli generate -i https://www.edifabric.com/docs/edifabric-cloud/openapi-v3.json -g python -o ./edifabric-cloud-python
```

| Language | Generator | Options |
|---|---|---|
| C# / .NET | [`csharp`](https://openapi-generator.tech/docs/generators/csharp/) | `--additional-properties=packageName=EdiFabric.Cloud,targetFramework=net8.0` |
| Java | [`java`](https://openapi-generator.tech/docs/generators/java/) | `--additional-properties=library=native,groupId=com.edifabric,artifactId=edifabric-cloud` |
| Python | [`python`](https://openapi-generator.tech/docs/generators/python/) | `--additional-properties=packageName=edifabric_cloud` |
| TypeScript / Node.js | [`typescript-fetch`](https://openapi-generator.tech/docs/generators/typescript-fetch/) | `--additional-properties=npmName=edifabric-cloud` |
| Go | [`go`](https://openapi-generator.tech/docs/generators/go/) | `--additional-properties=packageName=edifabriccloud` |
| Rust | [`rust`](https://openapi-generator.tech/docs/generators/rust/) | `--additional-properties=packageName=edifabric-cloud` |
| PHP | [`php`](https://openapi-generator.tech/docs/generators/php/) | `--additional-properties=invokerPackage=EdiFabric\\Cloud` |
| Ruby | [`ruby`](https://openapi-generator.tech/docs/generators/ruby/) | `--additional-properties=gemName=edifabric_cloud` |
| Kotlin | [`kotlin`](https://openapi-generator.tech/docs/generators/kotlin/) | `--additional-properties=packageName=com.edifabric.cloud` |
| Swift | [`swift5`](https://openapi-generator.tech/docs/generators/swift5/) | `--additional-properties=projectName=EdiFabricCloud` |

Other generators read the same files:

- [Postman](https://learning.postman.com/docs/sdk-generator/overview): import `v3/openapi.json` or `v2/openapi.json` as a collection to call the API from Postman, and generate an SDK from it in TypeScript, Python, Java, Kotlin, C#, Go, PHP, Ruby or Rust.
- [Kiota](https://learn.microsoft.com/openapi/kiota/), [NSwag](https://github.com/RicoSuter/NSwag) and [openapi-typescript](https://openapi-ts.dev/) for C#, Go, Java, PHP, Python and TypeScript clients.

The API definitions describe the transaction content of each X12Interchange as a free-form object, because its properties depend on the transaction. For typed classes of a transaction, generate them from its OpenEDI template.

## Generate classes from an OpenEDI template

An OpenEDI template is an OpenAPI 3 document whose schemas are the transaction's loops, segments and data elements, with the same property names as the API's JSON. Pick one from [`openedi/`](openedi/README.md) and point a generator at it:

```bash
openapi-generator-cli generate -i openedi/x12/hipaa/005010/837p/en-837P-openedi.json -g java --global-property models -o ./java
datamodel-codegen --input openedi/x12/hipaa/005010/837p/en-837P-openedi.json --input-file-type openapi --output hipaa_837p.py
```

[EDI models and code generation](https://www.edifabric.com/docs/getting-started/edi-models.html) has the generator for each language, and how to fill the classes from Parse output and pass them to Build. To change a template for a trading partner, open it in the [EDI Spec Builder](https://www.edifabric.com/spec-builder/index.html). The [OpenEDI format](https://www.edifabric.com/docs/getting-started/openedi-format.html) describes every extension the templates use.

## Run the API offline

ediFabric Native runs the same X12 operations inside your process, so EDI files never leave your network. These examples implement the v2 and v3 X12 endpoints of this API with Native:

- [Azure Functions](https://github.com/EdiFabric/API.Azure)
- [AWS Lambda](https://github.com/EdiFabric/API.AWS)
- [ASP.NET Core](https://github.com/EdiFabric/API.ASPNET)

## More

- [ediFabric Cloud documentation](https://www.edifabric.com/docs/edifabric-cloud/introduction.html)
- [API status](https://www.edifabric.com/edination/api-status.html)
- [EDI spec library](https://www.edifabric.com/specs/index.html)
- [Support](https://www.edifabric.com/support.html)

Use of the API is subject to the [ediFabric End User License Agreement](https://www.edifabric.com/files/eula.pdf). See [LICENSE.md](LICENSE.md).
