---
title: Úloha VerifyFileHash | Microsoft Docs
description: Přečtěte si, jak nástroj MSBuild používá úlohu VerifyFileHash k ověření, že soubor odpovídá očekávané hodnotě hash souboru, a pokud se neshoduje, dojde k chybě.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cfd6bb88a5bfbbffb7c99f7f43036cf9fee4d6ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908806"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash – úloha

Ověřuje, že soubor odpovídá očekávané hodnotě hash souboru. Pokud se hodnota hash neshoduje, úloha se nezdařila.

Tato úloha se přidala do 15,8, ale vyžaduje [alternativní řešení](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pro použití ve verzích MSBuild pod 16,0.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `VerifyFileHash` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Požadovaný parametr `String`.<br /><br />Soubor, který se má vyhodnotit a ověřit|
|`Hash`|Požadovaný parametr `String`.<br /><br />Očekávaná hodnota hash souboru.|
|`Algorithm`|Volitelný `String` parametr.<br /><br />Algoritmus. Povolené hodnoty: `SHA256` , `SHA384` , `SHA512` . Výchozí nastavení = `SHA256` .|
|`HashEncoding`|Volitelný `String` parametr.<br /><br />Kódování, které má být použito pro vygenerované hodnoty hash. Výchozí hodnota je `hex` . Povolené hodnoty = `hex` , `base64` .|

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
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
