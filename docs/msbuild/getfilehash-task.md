---
title: Úloha GetFileHash | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8f3de9a4f2fe848e1cbd41e14e82498845ca2cf
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578661"
---
# <a name="getfilehash-task"></a>GetFileHash – úloha

Vypočítá kontrolní součet obsahu souboru nebo sady souborů.

Tato úloha se přidala do 15,8, ale vyžaduje [alternativní řešení](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pro použití ve verzích MSBuild pod 16,0.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry úlohy `GetFileHash`.

|Parametr|Popis|
|---------------|-----------------|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Soubory, které se mají vyhodnotit.|
|`Items`|výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Vstupní `Files` s dalšími metadaty nastavenými na hodnotu hash souboru.|
|`Hash`|výstupní parametr `String`.<br /><br />Hodnota hash souboru Tento výstup je nastaven pouze v případě, že byla předána právě jedna položka.|
|`Algorithm`|Volitelný parametr `String`.<br /><br />Algoritmus. Povolené hodnoty: `SHA256`, `SHA384``SHA512`. Výchozí hodnota = `SHA256`.|
|`MetadataName`|Volitelný parametr `String`.<br /><br />Název metadat, ve kterém je hodnota hash uložena v každé položce. Výchozí hodnota je `FileHash`.|
|`HashEncoding`|Volitelný parametr `String`.<br /><br />Kódování, které má být použito pro vygenerované hodnoty hash. Výchozí hodnota je `hex`. Povolené hodnoty = `hex`, `base64`.|

## <a name="example"></a>Příklad

Následující příklad používá úlohu `GetFileHash` k určení a tisku kontrolního součtu položek `FilesToHash`.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)