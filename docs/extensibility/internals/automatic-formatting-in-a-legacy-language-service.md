---
title: Automatické formátování ve službě staršího jazyka | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709981"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatické formátování ve starší jazykové službě
Při automatickém formátování služba jazyka automaticky vloží úryvek kódu, když uživatel začne zadávat známý kód.

## <a name="automatic-formatting-behavior"></a>Automatické formátování
 Například když *zadáte*if , služba jazyka automaticky vloží odpovídající závorky, nebo pokud stisknete klávesu ENTER, služba jazyka vynutí textový kurzor na novém řádku na příslušnou úroveň odsazení, v závislosti na tom, zda předchozí řádek otevře nový obor.

 Příkazový filtr použitý pro zbytek služby jazyka lze použít také pro automatické formátování. Můžete také zvýraznit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>odpovídající závorky voláním .

## <a name="see-also"></a>Viz také
- [Vývoj služby starších jazyků](../../extensibility/internals/developing-a-legacy-language-service.md)
