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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 60093d237ed2aa7a14e5695efc66fe8edd515f4a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062392"
---
# <a name="vscodewindowmanager-object"></a>Objekt VSCodeWindowManager

Jazyková služba implementuje správce oken kódu a zodpovídá za správu doplňků (například rozevírací panel). Další informace najdete v tématu [přizpůsobení oken kódu pomocí starší verze rozhraní API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

V následující tabulce jsou uvedena rozhraní v `VSCodeWindowManager` objektu.

|Rozhraní|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Umožňuje přidat nebo odebrat doplňky (například rozevírací panely) v okně kódu.|