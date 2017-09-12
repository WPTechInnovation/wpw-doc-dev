# .NET Worldpay Within wrapper

## Introduction

The .NET Worldpay Within wrapper provides a convenient entry point for application developers who wish to create applications using the Worldpay Within toolkit.

Currently, this is built against .NET Framework 4.5.2, however I intend to make this available for use in portable DLLs (to work on Android, iOS) as well as .NET Core, so it can be easily used from Linux and Mac-based operating systems as well.

## Prerequisites

This has been created and built using Microsoft Visual Studio 2015 Community Edition.

## Building

Skip this if you just want to use the pre-built DLLs for using Worldpay Within.

Use nuget to acquire the 0.9.3 Apache Thrift libraries using the following command from the nugen package console:

`Install-Package ApacheThrift -Version 0.9.3`

If you don't specify the version, as of 16/6/15 you'll get an old version which will result in missing type errors (e.g. `'TProtocol' does not contain a definition for 'IncrementRecursionDepth'`).

### Worldpay.Within.Rpc

This project contains nothing but the generated RPC wrappers for Thrift.

You can rebuild this code by running:

`thrift-0.9.3.exe -r -out %GOPATH%\src\innovation.worldpay.com\worldpay-within-sdk\wrappers\dotnet\Worldpay.Within\Worldpay.Within.Rpc --gen csharp:nullable,union %GOPATH%\src\innovation.worldpay.com\worldpay-within-sdk\rpc\wpwithin.thrift`

> The -r is there just for safety, in case subdirectories are used in future for storing dependent Thrift IDL files.

Note, the full set of options for the Thrift compiler are as follows (we might want to use this later, holding off for now in the name of simplicity):

    async:           Adds Async support using Task.Run.
    asyncctp:        Adds Async CTP support using TaskEx.Run.
    wcf:             Adds bindings for WCF to generated classes.
    serial:          Add serialization support to generated classes.
    nullable:        Use nullable types for properties.
    hashcode:        Generate a hashcode and equals implementation for classes.
    union:           Use new union typing, which includes a static read function for union types.

Be sure to refresh the project source tree in Visual Studio to ensure that any newly generated files are included in the project. If you fail to do this, expect compile errors for missing types to be thrown.

## Using

To use Worldpay Within, add the following DLLs to your project path:

1.  `Worldpay.Within.dll` - this contains the wrapper code and Apache Thrift generated C# wrapper code.
2.  `Thrift.dll` - Apache Thrift library.
3.  `Logging Framework` - whatever logging framework we're going to use.