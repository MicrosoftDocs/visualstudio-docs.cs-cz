---
title: Objekt VSCodeWindowManager | Microsoft Docs
description: Seznamte se s objektem VSCodeWindowManager, který zodpovídá za správu doplňků, například na rozevírací panel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5c602a1cf46382e5a8b5c688501b2406e4a6d0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863997"
---
# <a name="vscodewindowmanager-object"></a>Objekt VSCodeWindowManager

Jazyková služba implementuje správce oken kódu a zodpovídá za správu doplňků (například rozevírací panel). Další informace najdete v tématu [přizpůsobení oken kódu pomocí starší verze rozhraní API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

V následující tabulce jsou uvedena rozhraní v `VSCodeWindowManager` objektu.

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Umožňuje přidat nebo odebrat doplňky (například rozevírací panely) v okně kódu.|