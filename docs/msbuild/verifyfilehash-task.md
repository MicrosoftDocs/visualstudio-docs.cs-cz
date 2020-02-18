---
title: Úloha VerifyFileHash | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9340657704900feb5ebdc188103109872ee39f5d
ms.sourcegitcommit: e3b9cbeea282f1b531c6a3f60515ebfe1688aa0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/18/2020
ms.locfileid: "77439116"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash – úloha

Ověřuje, že soubor odpovídá očekávané hodnotě hash souboru. Pokud se hodnota hash neshoduje, úloha se nezdařila.

Tato úloha se přidala do 15,8, ale vyžaduje [alternativní řešení](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pro použití ve verzích MSBuild pod 16,0.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry úlohy `VerifyFileHash`.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Vyžaduje se `String` parametr.<br /><br />Soubor, který se má vyhodnotit a ověřit|
|`Hash`|Vyžaduje se `String` parametr.<br /><br />Očekávaná hodnota hash souboru.|
|`Algorithm`|Volitelný parametr `String`.<br /><br />Algoritmus. Povolené hodnoty: `SHA256`, `SHA384``SHA512`. Výchozí hodnota = `SHA256`.|
|`HashEncoding`|Volitelný parametr `String`.<br /><br />Kódování, které má být použito pro vygenerované hodnoty hash. Výchozí hodnota je `hex`. Povolené hodnoty = `hex`, `base64`.|

## <a name="example"></a>Příklad

Následující příklad používá úlohu `VerifyFileHash` k ověření vlastního kontrolního součtu.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

Pokud nechcete, aby sestavení selhalo, pokud se hodnota hash neshoduje, například pokud používáte porovnání hodnoty hash jako podmínku pro tok řízení, můžete na základě tohoto kódu downgrade upozornění na zprávu. 16,5

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
