# Cloudflare Workers and KV Demo
A Cloudflare Workers and KV Demo by wrangler


Step1. Install wrangler
---------------------
[Install/Update Wrangler](https://developers.cloudflare.com/workers/wrangler/install-and-update/).

```
$ npm install wrangler
```

Step2. Create a KV namespace (parameter) with Wrangler
---------------------
[Workers KV](https://developers.cloudflare.com/workers/wrangler/workers-kv/#create-a-kv-namespace-with-wrangler).

```
$ wrangler kv:namespace create parameter
 ⛅️ wrangler 3.0.1
------------------
▲ [WARNING] No configured name present, using `worker` as a prefix for the title


🌀 Creating namespace with title "worker-parameter"
✨ Success!
Add the following to your configuration file in your kv_namespaces array:
{ binding = "parameter", id = "4c8ebcd1017c4fb0af5503cd6113efdc" }
```

Step3. Build Cloudflare Workers and KV Demo
---------------------

Clone the project

```
$ git clone https://github.com/jason61306/Cloudflare_Workers_KV_Demo.git
```
Modify wrangler.toml to add the id from step2

[Wrangler commands](https://developers.cloudflare.com/workers/wrangler/commands).

```
name = "kv_test"
main = "src/worker.js"
compatibility_date = "2023-08-01"

# Bind a KV Namespace. Use KV as persistent storage for small key-value pairs.
# Docs: https://developers.cloudflare.com/workers/runtime-apis/kv
 [[kv_namespaces]]
 binding = "parameter"
 id = "{id}"
 [vars]
 DEFAULT_KV_NAMESPACE = "parameter"

```
build by wrangler

```
$ cd Cloudflare_Workers_KV_Demo
```

```
$ wrangler deploy
⛅️ wrangler 3.0.1
------------------
Your worker has access to the following bindings:
- KV Namespaces:
  - parameter: 4c8ebcd1017c4fb0af5503cd6113efdc
Total Upload: 0.47 KiB / gzip: 0.29 KiB
Uploaded kv_test (1.42 sec)
Published kv_test (4.32 sec)
  https://kv_test.jason61306.workers.dev
Current Deployment ID: dcca63d6-1d3c-4946-a81d-a785dc628d83
```

The Result
---------------------
Visit the following link and add parameters, the parameters would be stored in KV.

**https://kv_test.jason61306.workers.dev**

For Example:

[https://kv_test.jason61306.workers.dev?p1=test1&p2=test2](https://kv_test.jason61306.workers.dev?p1=test1&p2=test2)

Result:

![image](https://github.com/jason61306/Cloudflare_Workers_KV_Demo/blob/master/KV.png)




