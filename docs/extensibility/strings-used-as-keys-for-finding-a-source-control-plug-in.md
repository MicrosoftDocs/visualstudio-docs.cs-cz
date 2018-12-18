---
title: Řetězce, které jsou použity jako klíče pro vyhledání modulu Plug-in zdrojového kódu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a42eebe67ce1f611cf6e48883bc09139f241e658
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137671"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Řetězce, které jsou použity jako klíče pro vyhledání modulu Plug-in zdrojového kódu
Následující řetězce jsou klíče pro přístup k registru k nalezení informací o ovládacím prvku modulu plug-in.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, a `STR_SCCPROVIDERNAME` jsou klíče registru nebo hodnoty používá k registraci knihovny DLL jako modul plug-in Správa zdrojového kódu pro Visual Studio.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, a `SCC_STATUS_FILE` se používají k popisu formátu MSSCCPRJ. SCC soubor.  
  
## <a name="string-keys-and-values"></a>Řetězec klíče a hodnoty  
  
|Key|Hodnota|  
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
|`SCC_FILE_SIGNATURE`|Soubor ovládacího prvku zdrojového kódu|  
|`SCC_NSE`|Namespace rozšíření|  
|`SCC_NSE_PREFIX`|Předpona Protocal|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in programu zdroj ovládacího prvku](../extensibility/source-control-plug-ins.md)   
 [Postupy: Instalace modulu Plug-in Správa zdrojového kódu](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Soubor MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)