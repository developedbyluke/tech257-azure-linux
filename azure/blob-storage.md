#### Create a Storage Container

To create a container within a storage account:

```shell
az storage container create --account-name <storage_account_name> --name <container_name> --auth-mode login
```

#### Delete a Storage Container

To delete a container from a storage account:

```shell
az storage container delete --account-name <storage_account_name> --name <container_name> --auth-mode login
```

#### List Storage Containers

To list all containers within a storage account:

```shell
az storage container list --account-name <storage_account_name> --auth-mode login --output table
```

Use `--query "[].{ Name:name }"` to format the output to only show container names.

#### Upload a Blob to a Container

To upload a file as a blob into a specific container:

```shell
az storage blob upload --account-name <storage_account_name> --container-name <container_name> --name <blob_name> --file <path_to_file> --auth-mode login
```

#### Delete a Blob

To delete a blob from a container:

```shell
az storage blob delete --account-name <storage_account_name> --container-name <container_name> --name <blob_name> --auth-mode login
```

#### List Blobs in a Container

To list all blobs within a specific container:

```shell
az storage blob list --account-name <storage_account_name> --container-name <container_name> --output table --auth-mode login
```

#### Download a Blob

To download a blob from a container:

```shell
az storage blob download --account-name <storage_account_name> --container-name <container_name> --name <blob_name> --file <path_to_download> --auth-mode login
```

#### Set Container Public Access Level

To modify the public access level of a container:

```shell
az storage container set-permission --account-name <storage_account_name> --name <container_name> --public-access off|blob|container --auth-mode login
```
