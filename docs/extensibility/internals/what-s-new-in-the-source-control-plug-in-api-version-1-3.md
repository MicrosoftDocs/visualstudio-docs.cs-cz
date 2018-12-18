---
title: Co&#39;s ve zdroji řízení verze rozhraní API modulu Plug-in 1.3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abeb2a0a936a5d706e2e3744e9dd0f4e3123bdbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31145006"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Co&#39;s ve zdroji řízení verze rozhraní API modulu Plug-in 1.3
Zdroj ovládacího prvku Plug-in API verze 1.3 zavádí následující nové funkce k poskytování pokročilejší řízení.  
  
## <a name="changes"></a>Změny  
 Zdroj ovládacího prvku Plug-in API verze 1.3 přibyly následující funkce:  
  
|Funkce|Přehled|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Povoluje další funkce bits, aby byly hlášené|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Umožňuje zkoumání souborů, které mají novější verze v databázi řízení verze než na místním disku|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Umožňuje prozkoumání stavu změny názvu (přejmenování, přidání a odstranění) pro zadané soubory|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Umožňuje prozkoumání adresářů a souborů v databázi verze ovládacího prvku|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Přidá zadaný seznam souborů z verze databáze ovládacího prvku do aktuálního projektu|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Provede tichou "Get" zadané soubory (zobrazené žádné uživatelské rozhraní)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Umožňuje přístup k možnosti specifické pro uživatele|  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)