# cloudpathlib Changelog

## v0.10.0 (2022-08-18)

 - API change: Make `stat` on base class method instead of property to follow `pathlib` ([Issue #234](https://github.com/drivendataorg/cloudpathlib/issues/234), [PR #250](https://github.com/drivendataorg/cloudpathlib/pull/250))
 - Fixed "S3Path.exists() returns True on partial matches." ([Issue #208](https://github.com/drivendataorg/cloudpathlib/issues/208), [PR #244](https://github.com/drivendataorg/cloudpathlib/pull/244))
 - Make `AnyPath` subclass of `AnyPath` ([Issue #246](https://github.com/drivendataorg/cloudpathlib/issues/246), [PR #251](https://github.com/drivendataorg/cloudpathlib/pull/251))
 - Skip docstrings if not present to avoid failing under `-00` ([Issue #238](https://github.com/drivendataorg/cloudpathlib/issues/238), [PR #249](https://github.com/drivendataorg/cloudpathlib/pull/249))
 - Add `py.typed` file so mypy runs ([Issue #243](https://github.com/drivendataorg/cloudpathlib/issues/243), [PR #248](https://github.com/drivendataorg/cloudpathlib/pull/248))

## v0.9.0 (2022-06-03)
 - Added `absolute` to `CloudPath` (does nothing as `CloudPath` is always absolute) ([PR #230](https://github.com/drivendataorg/cloudpathlib/pull/230))
 - Added `resolve` to `CloudPath` (does nothing as `CloudPath` is resolved in advance) ([Issue #151](https://github.com/drivendataorg/cloudpathlib/issues/151), [PR #230](https://github.com/drivendataorg/cloudpathlib/pull/230))
 - Added `relative_to` to `CloudPath` which returns a `PurePosixPath` ([Issue #149](https://github.com/drivendataorg/cloudpathlib/issues/149), [PR #230](https://github.com/drivendataorg/cloudpathlib/pull/230))
 - Added `is_relative_to` to `CloudPath` ([Issue #149](https://github.com/drivendataorg/cloudpathlib/issues/149), [PR #230](https://github.com/drivendataorg/cloudpathlib/pull/230))
 - Added `is_absolute` to `CloudPath` (always true as `CloudPath` is always absolute) ([PR #230](https://github.com/drivendataorg/cloudpathlib/pull/230))
 - Accept and delegate `read_text` parameters to cached file ([PR #230](https://github.com/drivendataorg/cloudpathlib/pull/230))
 - Added `exist_ok` parameter to `touch` ([PR #230](https://github.com/drivendataorg/cloudpathlib/pull/230))
 - Added `missing_ok` parameter to `unlink`, which defaults to True. This diverges from pathlib to maintain backward compatibility ([PR #230](https://github.com/drivendataorg/cloudpathlib/pull/230))
 - Fixed missing root object entries in documentation's Intersphinx inventory ([Issue #211](https://github.com/drivendataorg/cloudpathlib/issues/211), [PR #237](https://github.com/drivendataorg/cloudpathlib/pull/237))

## v0.8.0 (2022-05-19)

 - Fixed pickling of `CloudPath` objects not working. ([Issue #223](https://github.com/drivendataorg/cloudpathlib/issues/223), [PR #224](https://github.com/drivendataorg/cloudpathlib/pull/224))
 - Added functionality to [push the MIME (media) type to the content type property on cloud providers by default. ([Issue #222](https://github.com/drivendataorg/cloudpathlib/issues/222), [PR #226](https://github.com/drivendataorg/cloudpathlib/pull/226))

## v0.7.1 (2022-04-06)

- Fixed inadvertent inclusion of tests module in package. ([Issue #173](https://github.com/drivendataorg/cloudpathlib/issues/173), [PR #219](https://github.com/drivendataorg/cloudpathlib/pull/219))

## v0.7.0 (2022-02-16)

- Fixed `glob` and `rglob` functions by using pathlib's globbing logic rather than fnmatch. ([Issue #154](https://github.com/drivendataorg/cloudpathlib/issues/154))
- Fixed `iterdir` to not include self. ([Issue #15](https://github.com/drivendataorg/cloudpathlib/issues/15))
- Fixed error when calling `suffix` and `suffixes` on a cloud path with no suffix. ([Issue #120](https://github.com/drivendataorg/cloudpathlib/issues/120))
- Changed `parents` return type from list to tuple, to better match pathlib's tuple-like `_PathParents` return type.
- Remove support for Python 3.6. [Issue #186](https://github.com/drivendataorg/cloudpathlib/issues/186)

## v0.6.5 (2022-01-25)

- Fixed error when "directories" created on AWS S3 were reported as files. ([Issue #148](https://github.com/drivendataorg/cloudpathlib/issues/148), [PR #190](https://github.com/drivendataorg/cloudpathlib/pull/190))
- Fixed bug where GCE machines can instantiate default client, but we don't attempt it. ([Issue #191](https://github.com/drivendataorg/cloudpathlib/issues/191)
- Support `AWS_ENDPOINT_URL` environment variable to set the `endpoint_url` for `S3Client`. ([PR #193](https://github.com/drivendataorg/cloudpathlib/pull/193))

## v0.6.4 (2021-12-29)

- Fixed error where `BlobProperties` type hint causes import error if Azure dependencies not installed.

## v0.6.3 (2021-12-29)

- Fixed error when using `rmtree` on nested directories for Google Cloud Storage and Azure Blob Storage. ([Issue #184](https://github.com/drivendataorg/cloudpathlib/issues/184), [PR #185](https://github.com/drivendataorg/cloudpathlib/pull/185))
- Fixed broken builds due mypy errors in azure dependency ([PR #177](https://github.com/drivendataorg/cloudpathlib/pull/177))
- Fixed dev tools for building and serving documentation locally ([PR #178](https://github.com/drivendataorg/cloudpathlib/pull/178))

## v0.6.2 (2021-09-20)

- Fixed error when importing `cloudpathlib` for missing `botocore` dependency when not installed with S3 dependencies. ([PR #168](https://github.com/drivendataorg/cloudpathlib/pull/168))

## v0.6.1 (2021-09-17)

- Fixed absolute documentation URLs to point to the new versioned documentation pages.
- Fixed bug where `no_sign_request` couldn't be used to download files since our code required list permissions to the bucket to do so. ([Issue #169](https://github.com/drivendataorg/cloudpathlib/issues/169), [PR #168](https://github.com/drivendataorg/cloudpathlib/pull/168)).

## v0.6.0 (2021-09-07)

- Added `no_sign_request` parameter to `S3Client` instantiation for anonymous requests for public resources on S3. See [documentation](https://cloudpathlib.drivendata.org/stable/api-reference/s3client/#cloudpathlib.s3.s3client.S3Client.__init__) for more details. ([#164](https://github.com/drivendataorg/cloudpathlib/pull/164))

## v0.5.0 (2021-08-31)

- Added `boto3_transfer_config` parameter to `S3Client` instantiation, which allows passing a `boto3.s3.transfer.TransferConfig` object and is useful for controlling multipart and thread use in uploads and downloads. See [documentation](https://cloudpathlib.drivendata.org/stable/api-reference/s3client/#cloudpathlib.s3.s3client.S3Client.__init__) for more details. ([#150](https://github.com/drivendataorg/cloudpathlib/pull/150))

## v0.4.1 (2021-05-29)

- Added support for custom S3-compatible object stores. This functionality is available via the `endpoint_url` keyword argument when instantiating an `S3Client` instance. See [documentation](https://cloudpathlib.drivendata.org/stable/authentication/#accessing-custom-s3-compatible-object-stores) for more details. ([#138](https://github.com/drivendataorg/cloudpathlib/pull/138) thanks to [@YevheniiSemendiak](https://github.com/YevheniiSemendiak))
- Added `CloudPath.upload_from` which uploads the passed path to this CloudPath (issuse [#58](https://github.com/drivendataorg/cloudpathlib/issues/58))
- Added support for common file transfer functions based on `shutil`. Issue [#108](https://github.com/drivendataorg/cloudpathlib/issues/108). PR [#142](https://github.com/drivendataorg/cloudpathlib/pull/142).
  - `CloudPath.copy` copy a file from one location to another. Can be cloud -> local or cloud -> cloud. If `client` is not the same, the file transits through the local machine.
  - `CloudPath.copytree` reucrsively copy a directory from one location to another. Can be cloud -> local or cloud -> cloud. Uses `CloudPath.copy` so if `client` is not the same, the file transits through the local machine.

## v0.4.0 (2021-03-13)

- Added rich comparison operator support to cloud paths, which means you can now use them with `sorted`. ([#129](https://github.com/drivendataorg/cloudpathlib/pull/129))
- Added polymorphic class `AnyPath` which creates a cloud path or `pathlib.Path` instance appropriately for an input filepath. See new [documentation](https://cloudpathlib.drivendata.org/stable/anypath-polymorphism/) for details and example usage. ([#130](https://github.com/drivendataorg/cloudpathlib/pull/130))
- Added integration with [Pydantic](https://pydantic-docs.helpmanual.io/). See new [documentation](https://cloudpathlib.drivendata.org/stable/integrations/#pydantic) for details and example usage. ([#130](https://github.com/drivendataorg/cloudpathlib/pull/130))
- Exceptions: ([#131](https://github.com/drivendataorg/cloudpathlib/pull/131))
    - Changed all custom `cloudpathlib` exceptions to be located in new `cloudpathlib.exceptions` module.
    - Changed all custom `cloudpathlib` exceptions to subclass from new base `CloudPathException`. This allows for easy catching of any custom exception from `cloudpathlib`.
    - Changed all custom exceptions names to end with `Error` as recommended by [PEP 8](https://www.python.org/dev/peps/pep-0008/#exception-names).
    - Changed various functions to throw new `CloudPathFileExistsError`, `CloudPathIsADirectoryError` or `CloudPathNotADirectoryError` exceptions instead of a generic `ValueError`.
    - Removed exception exports from the root `cloudpathlib` package namespace. Import from `cloudpathlib.exceptions` instead if needed.
- Fixed `download_to` method to handle case when source is a file and destination is a directory. ([#121](https://github.com/drivendataorg/cloudpathlib/pull/121) thanks to [@genziano](https://github.com/genziano))
- Fixed bug where `hash(...)` of a cloud path was not consistent with the equality operator. ([#129](https://github.com/drivendataorg/cloudpathlib/pull/129))
- Fixed `AzureBlobClient` instantiation to throw new error `MissingCredentialsError` when no credentials are provided, instead of `AttributeError`. `LocalAzureBlobClient` has also been changed to accordingly error under those conditions. ([#131](https://github.com/drivendataorg/cloudpathlib/pull/131))
- Fixed `GSClient` to instantiate as anonymous with public access only when instantiated with no credentials, instead of erroring. ([#131](https://github.com/drivendataorg/cloudpathlib/pull/131))

## v0.3.0 (2021-01-29)

- Added a new module `cloudpathlib.local` with utilities for mocking cloud paths in tests. The module has "Local" substitute classes that use the local filesystem in place of cloud storage. See the new documentation article ["Testing code that uses cloudpathlib"](https://cloudpathlib.drivendata.org/stable/testing_mocked_cloudpathlib/) to learn more about how to use them. ([#107](https://github.com/drivendataorg/cloudpathlib/pull/107))

## v0.2.1 (2021-01-25)

- Fixed bug where a `NameError` was raised if the Google Cloud Storage dependencies were not installed (even if using a different storage provider).

## v0.2.0 (2021-01-23)

- Added support for Google Cloud Storage. Instantiate with URIs prefixed by `gs://` or explicitly using the `GSPath` class. ([#113](https://github.com/drivendataorg/cloudpathlib/pull/113) thanks to [@wolfgangwazzlestrauss](https://github.com/wolfgangwazzlestrauss))
- Changed backend logic to reduce number of network calls to cloud. This should result in faster cloud path operations, especially when dealing with many small files. ([#110](https://github.com/drivendataorg/cloudpathlib/issues/110), [#111](https://github.com/drivendataorg/cloudpathlib/pull/111))

## v0.1.2 (2020-11-14)

- Fixed `CloudPath` instantiation so that reinstantiating with an existing `CloudPath` instance will reuse the same client, if a new client is not explicitly passed. This addresses the edge case of non-idempotency when reinstantiating a `CloudPath` instance with a non-default client. ([#104](https://github.com/drivendataorg/cloudpathlib/pull/104))

## v0.1.1 (2020-10-15)

- Fixed a character-encoding bug when building from source on Windows. ([#98](https://github.com/drivendataorg/cloudpathlib/pull/98))

## v0.1.0 (2020-10-06)

- Initial release of cloudpathlib with support for Amazon S3 and Azure Blob Storage! 🎉
