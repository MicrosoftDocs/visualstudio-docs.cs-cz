---
title: Ověřit Úkol SouborHash | Dokumenty společnosti Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53819a642edcdf0419dd445ac32dbde8d14ffb22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579523"
---
# <a name="verifyfilehash-task"></a>Úloha VerifyFileHash

Ověří, zda soubor odpovídá očekávané hodnotě hash souboru. Pokud se hash neshoduje, úkol se nezdaří.

Tato úloha byla přidána v 15.8, ale vyžaduje [řešení](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pro použití pro verze MSBuild pod 16.0.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `VerifyFileHash` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Požadovaný parametr `String`.<br /><br />Soubor, který má být zapisován a ověřen.|
|`Hash`|Požadovaný parametr `String`.<br /><br />Očekávaná hodnota hash souboru.|
|`Algorithm`|Volitelný `String` parametr.<br /><br />Algoritmus. Povolené `SHA256`hodnoty: `SHA384` `SHA512`, , . Výchozí `SHA256`= .|
|`HashEncoding`|Volitelný `String` parametr.<br /><br />Kódování, které se má použít pro generované hashe. Výchozí hodnota `hex`je na . Povolené hodnoty `hex` `base64`= , .|

## <a name="example"></a>Příklad

Následující příklad používá `VerifyFileHash` úlohu k ověření vlastního kontrolního součtu.

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

Na MSBuild 16.5 a novější, pokud nechcete, aby sestavení nezdaří, když se neshoduje hash, například pokud používáte porovnání hash jako podmínku pro tok řízení, můžete downgrade upozornění na zprávu pomocí následujícího kódu:

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
