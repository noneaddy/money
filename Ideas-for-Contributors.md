## Support for iOS Dynamic Analysis

A dynamic analysis module capable of performing runtime security analysis of iOS applications by instrumenting iOS  API calls. This can be implemented using Frida, an instrumentation framework. The user should be able to convert their iOS device into a pentesting device after running a script. They should then configure it with MobSF so that  it can use it for Dynamic Analysis of iOS Application

## Android x86 Frida Support

Frida is an excellent instrumentation framework (https://www.frida.re/). They support ARM Android but x86 support is limited. We need an x86 port of frida server to be used with MobSF android VM. Once that is completed, frida modules needs to be implemented to instrument critical Android APIs such as Bluetooth, SMS, Telephony, Crypto, File IO, Network etc.

## Improved Static Analysis of Windows Mobile App and iOS

Develop a Check list to identify security issues in iOS applications written in Swift. At the moment MobSF supports static analysis of Windows mobile binaries. We need to extend this to support static analysis of Windows Mobile Source code to identify vulnerabilities.

