---
title: Co&#39;s Novinkou v rozhraní Plug-in Plug-in API správy zdrojového kódu verze 1.3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703365"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Co&#39;s novinkou v rozhraní Plug-in API pro správu zdrojového kódu verze 1.3
Rozhraní Api plug-in source control verze 1.3 zavádí následující nové funkce, které poskytují pokročilejší řízení.

## <a name="changes"></a>Změny
 Následující funkce jsou nové pro rozhraní PLUG-IN Source Control API verze 1.3:

|Funkce|Přehled|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Umožňuje vykazovat další bity schopností.|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Umožňuje kontrolu souborů, které mají novější verze v databázi správy verzí než na místním disku|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Umožňuje kontrolu stavu změn názvu (přejmenování, přidání a odstranění) pro zadané soubory|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Umožňuje kontrolu adresářů a souborů v databázi správy verzí|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Přidá zadaný seznam souborů z databáze správy verzí do aktuálního projektu.|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Provede tichý "Get" zadaných souborů (není zobrazeno žádné uživatelské rozhraní)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Umožňuje přístup k možnostem specifickým pro uživatele|

## <a name="see-also"></a>Viz také
- [Začínáme](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
