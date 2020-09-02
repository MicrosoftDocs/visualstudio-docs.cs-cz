---
title: Migrace 64 registrace třídy modelu COM ladicího programu | Microsoft Docs
ms.date: 11/10/2016
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: jillfra
ms.workload:
- greggm
ms.openlocfilehash: 74fbb959f8272be001aad8a576724d5eb1ad6157
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62433692"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrace 64 registrace třídy modelu COM ladicího programu

Pro rozšíření ladicího programu, které registrují třídy COM v HKEY_CLASSES_ROOT pomocí modulu Regasm, regsvr32 nebo přímo zapisují do registru a jsou načteny do *msvsmon.exe* (vzdálený ladicí program), je nyní možné poskytnout tuto registraci msvsmon, aniž by bylo nutné zapisovat do HKEY_CLASSES_ROOT. To má vliv na starší verze filtru výrazů ladicího programu rozhraní .NET nebo moduly ladění, které jsou nakonfigurovány pro načtení v procesu *msvsmon.exe* .

## <a name="msvsmon-comclass-def"></a>Msvsmon-COMClass – def

Chcete-li použít tento postup, přidejte * *.msvsmon-comclass-def.js* do souboru vedle msvsmon (InstallDir:* \Common7\IDE\Remote Debugger\x64 *).

Zde je příklad souboru msvsmon-COMClass-def, který registruje jednu spravovanou a jednu nativní třídu:

Název souboru: *MyCompany.MyExample.msvsmon-comclass-def.jsna*

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
