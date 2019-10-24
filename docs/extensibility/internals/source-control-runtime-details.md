---
title: Podrobnosti o modulu runtime správy zdrojového kódu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d2469bc25fabd9659e09d6ca841ebc44a743cca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723399"
---
# <a name="source-control-runtime-details"></a>Podrobnosti modulu CLR správy zdrojového kódu
Projekt je přidán do správy zdrojového kódu, když uživatel přidá soubor do správy zdrojového kódu nebo prostřednictvím kontroleru automatizace, jako je například Průvodce. Projekt není určen pro sebe samé, že se nachází pod správou zdrojového kódu; podporuje správu zdrojového kódu, ale je nutné do něj přidat ručně.

## <a name="registering-with-a-source-control-package"></a>Registrace do balíčku správy zdrojového kódu
 Když je do správy zdrojového kódu přidán soubor v projektu, prostředí zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> k poskytnutí čtyř neprůhledných řetězců, které se používají jako soubory cookie systémem správy zdrojového kódu. Uložte tyto řetězce do souboru projektu. Tyto řetězce by měly být předány zástupnému kódu pro správu zdrojového kódu (součást sady Visual Studio, která spravuje balíčky správy zdrojových kódů) při spuštění typu projektu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Tím se zase načte příslušný balíček správy zdrojových kódů a předá se volání ke své implementaci `IVsSccManager2::RegisterSccProject`.

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)