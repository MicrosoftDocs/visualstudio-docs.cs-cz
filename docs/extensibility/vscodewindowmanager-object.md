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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e353070c780f69ea05c1c67986f7a40f34d0659c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925842"
---
# <a name="vscodewindowmanager-object"></a>Objekt VSCodeWindowManager

Jazyková služba implementuje správce oken kódu a zodpovídá za správu doplňků (například rozevírací panel). Další informace najdete v tématu [přizpůsobení oken kódu pomocí starší verze rozhraní API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

V následující tabulce jsou uvedena rozhraní v `VSCodeWindowManager` objektu.

|Rozhraní|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Umožňuje přidat nebo odebrat doplňky (například rozevírací panely) v okně kódu.|