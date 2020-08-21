---
title: Co &apos; je nového v rozhraní API modulu plug-in správy zdrojového kódu verze 1,3 | Microsoft Docs
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
ms.openlocfilehash: ec24e9ee3079d3b02ac13759b6ab5bdee8c07a84
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706448"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Co&#39;s novým v rozhraní API modulu plug-in správy zdrojového kódu verze 1,3
Rozhraní API pro modul plug-in správy zdrojového kódu verze 1,3 zavádí následující nové funkce, které poskytují pokročilejší kontrolu.

## <a name="changes"></a>Změny
 Následující funkce jsou v rozhraní API modulu plug-in správy zdrojového kódu nové verze 1,3:

|Funkce|Přehled|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Umožňuje nahlásit další možnosti v bitech.|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Umožňuje prozkoumání souborů, které mají novější verze v databázi správy verzí než na místním disku.|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Umožňuje vyzkoušení stavu změn názvů (přejmenování, přidávání a odstraňování) pro zadané soubory.|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Umožňuje prověřování adresářů a souborů v databázi správy verzí.|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Přidá zadaný seznam souborů z databáze správy verzí do aktuálního projektu.|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Provede tiché "Get" ze zadaných souborů (žádné uživatelské rozhraní není zobrazeno)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Umožňuje přístup k možnostem specifickým pro uživatele.|

## <a name="see-also"></a>Viz také:
- [Začínáme](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
