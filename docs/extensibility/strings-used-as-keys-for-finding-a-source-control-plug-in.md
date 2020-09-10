---
title: Řetězce používané jako klíče k vyhledání modulu plug-in správy zdrojového kódu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 038441f7bcea9fa1dafdd61505d4150ecf28a966
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741783"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Řetězce, které slouží jako klíče pro vyhledání modulu plug-in pro správu zdrojového kódu
Následující řetězce jsou klíče pro přístup k registru, aby bylo možné najít informace o modulu plug-in správy zdrojových kódů.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` a `STR_SCCPROVIDERNAME` jsou klíče registru nebo hodnoty používané k registraci DLL jako modul plug-in správy zdrojového kódu pro Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` , a `SCC_STATUS_FILE` se používají k popisu formátu MSSCCPRJ. Soubor SCC

## <a name="string-keys-and-values"></a>Klíče a hodnoty řetězců

|Klíč|Hodnota|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Správa zdrojového kódu|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Soubor řízení zdrojového kódu|
|`SCC_NSE`|Rozšíření oboru názvů|
|`SCC_NSE_PREFIX`|Protokolem předpona|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|Helpcollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Viz také:
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [Postupy: Instalace modulu plug-in správy zdrojového kódu](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Soubor MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
