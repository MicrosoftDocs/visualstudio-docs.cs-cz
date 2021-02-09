---
title: Úloha GetFileHash | Microsoft Docs
description: Naučte se pomocí úlohy MSBuild GetFileHash vypočítat kontrolní součty obsahu souboru nebo sady souborů.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 163fbfd9c2bf0ca56b5b9b6bc11dc48420cfc270
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914700"
---
# <a name="getfilehash-task"></a>GetFileHash – úloha

Vypočítá kontrolní součet obsahu souboru nebo sady souborů.

Tato úloha se přidala do 15,8, ale vyžaduje [alternativní řešení](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) pro použití ve verzích MSBuild pod 16,0.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `GetFileHash` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Soubory, které se mají vyhodnotit.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` výstupní parametr<br /><br />`Files`Vstup s dalšími metadaty nastavenými na hodnotu hash souboru.|
|`Hash`|`String` výstupní parametr<br /><br />Hodnota hash souboru Tento výstup je nastaven pouze v případě, že byla předána právě jedna položka.|
|`Algorithm`|Volitelný `String` parametr.<br /><br />Algoritmus. Povolené hodnoty: `SHA256` , `SHA384` , `SHA512` . Výchozí nastavení = `SHA256` .|
|`MetadataName`|Volitelný `String` parametr.<br /><br />Název metadat, ve kterém je hodnota hash uložena v každé položce. Výchozí hodnota je `FileHash` .|
|`HashEncoding`|Volitelný `String` parametr.<br /><br />Kódování, které má být použito pro vygenerované hodnoty hash. Výchozí hodnota je `hex` . Povolené hodnoty = `hex` , `base64` .|

## <a name="example"></a>Příklad

Následující příklad používá `GetFileHash` úlohu k určení a tisku kontrolního součtu `FilesToHash` položek.

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

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)