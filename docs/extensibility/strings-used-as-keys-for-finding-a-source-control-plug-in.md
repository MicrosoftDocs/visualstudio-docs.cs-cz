---
title: Řetězce používané jako klíče k vyhledání modulu plug-in správy zdrojového kódu
description: Přečtěte si o řetězcích, které jsou klíči pro přístup k registru, abyste našli informace o modulu plug-in správy zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f25a105c442fa4a1ff8ed0f95b9c49272d751932
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899379"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Řetězce, které slouží jako klíče pro vyhledání modulu plug-in pro správu zdrojového kódu
Následující řetězce jsou klíče pro přístup k registru pro vyhledání informací o modulu plug-in správy zdrojového kódu.

 `STR_SCC_PROVIDER_REG_LOCATION`, , a jsou klíče nebo hodnoty registru používané k registraci knihovny DLL jako `STR_PROVIDERREGKEY` modulu plug-in správy zdrojového kódu `STR_SCCPROVIDERPATH` `STR_SCCPROVIDERNAME` pro Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE` , a se používají k popisu `SCC_STATUS_FILE` formátu MSSCCPRJ. Soubor SCC.

## <a name="string-keys-and-values"></a>Řetězcové klíče a hodnoty

|Klíč|Hodnota|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Řízení zdrojového kódu|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|Scc|
|`SCC_FILE_SIGNATURE`|Řídicí soubor zdrojového kódu|
|`SCC_NSE`|Rozšíření oboru názvů|
|`SCC_NSE_PREFIX`|Protocal Prefix|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|Kolekce nápovědy|
|`STR_UI_LANGUAGE`|UiLanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [Postupy: Instalace modulu plug-in správy zdrojového kódu](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Soubor MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
