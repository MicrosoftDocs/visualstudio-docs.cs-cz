---
title: Automatické formátování ve službě starší verze jazyka | Microsoft Docs
description: Přečtěte si o automatickém formátování ve službě starší verze jazyka, která automaticky vloží fragment kódu, když začnete psát známou konstrukci kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651cecb20604069c6e8ccc5a5c7b983ab43d7384
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190054"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatické formátování ve službě starší verze jazyka
Při automatickém formátování vloží služba jazyka automaticky fragment kódu, když uživatel začne psát známou konstrukci kódu.

## <a name="automatic-formatting-behavior"></a>Chování automatického formátování
 *Pokud například zadáte,* že služba jazyka automaticky vloží odpovídající závorky nebo stisknete klávesu ENTER, služba Language vynutí kurzor na novém řádku na příslušné úrovni odsazení v závislosti na tom, zda předchozí řádek otevře nový obor.

 Filtr příkazů používaný pro zbytek jazykové služby lze použít také pro automatické formátování. Můžete také zvýraznit párové závorky voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Viz také
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
