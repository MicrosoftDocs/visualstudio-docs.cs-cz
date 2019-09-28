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
ms.openlocfilehash: 3acdaabffc35122616cced4113abbc5a43beb9a1
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481978"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash – úloha

Ověřuje, že soubor odpovídá očekávané hodnotě hash souboru.

Tato úloha se přidala do 15,8, ale vyžaduje [alternativní řešení](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pro použití ve verzích MSBuild pod 16,0.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `VerifyFileHash` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Povinný `String` parametr.<br /><br />Soubor, který se má vyhodnotit a ověřit|
|`Hash`|Povinný `String` parametr.<br /><br />Očekávaná hodnota hash souboru.|
|`Algorithm`|Volitelný `String` parametr.<br /><br />Algoritmus. Povolené hodnoty: `SHA256`, `SHA384` `SHA512`. Výchozí hodnota = `SHA256`.|
|`HashEncoding`|Volitelný `String` parametr.<br /><br />Kódování, které má být použito pro vygenerované hodnoty hash. Výchozí hodnota je `hex`. Povolené hodnoty = `hex`, `base64`.|

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

## <a name="see-also"></a>Viz také:

- [Úkoly](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)