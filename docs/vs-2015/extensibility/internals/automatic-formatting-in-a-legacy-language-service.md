---
title: Automatické formátování ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6183fc47138ebb5108e4fbbd2bfa407e5804a72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157272"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatické formátování ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při automatickém formátování vloží služba jazyka automaticky fragment kódu, když uživatel začne psát známou konstrukci kódu.  
  
## <a name="automatic-formatting-behavior"></a>Chování automatického formátování  
 Když například zadáte `if` , služba jazyka automaticky vloží odpovídající závorky, nebo pokud stisknete klávesu ENTER, vynutí služba jazyka kurzor na novém řádku na odpovídající úrovni odsazení v závislosti na tom, zda předchozí řádek otevře nový obor.  
  
 Filtr příkazů používaný pro zbytek jazykové služby lze použít také pro automatické formátování. Můžete také zvýraznit párové závorky voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .  
  
## <a name="see-also"></a>Viz také  
 [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
