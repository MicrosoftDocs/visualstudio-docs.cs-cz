---
title: Úkol GetFileHash | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77578661"
---
# <a name="getfilehash-task"></a>Úloha GetFileHash

Vypočítá kontrolní součty obsahu souboru nebo sady souborů.

Tato úloha byla přidána v 15.8, ale vyžaduje [řešení](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pro použití pro verze MSBuild pod 16.0.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `GetFileHash` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Soubory, které mají být zahasovány.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]`výstupního parametru.<br /><br />Vstup `Files` s dalšími metadaty nastavenými na hash souboru.|
|`Hash`|`String`výstupního parametru.<br /><br />Hash souboru. Tento výstup je nastaven pouze v případě, že byla předána přesně jedna položka.|
|`Algorithm`|Volitelný `String` parametr.<br /><br />Algoritmus. Povolené `SHA256`hodnoty: `SHA384` `SHA512`, , . Výchozí `SHA256`= .|
|`MetadataName`|Volitelný `String` parametr.<br /><br />Název metadat, kde je v každé položce uložena hash. Výchozí hodnota `FileHash`je na .|
|`HashEncoding`|Volitelný `String` parametr.<br /><br />Kódování, které se má použít pro generované hashe. Výchozí hodnota `hex`je na . Povolené hodnoty `hex` `base64`= , .|

## <a name="example"></a>Příklad

Následující příklad používá `GetFileHash` úlohu k určení a `FilesToHash` tisku kontrolního součtu položek.

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