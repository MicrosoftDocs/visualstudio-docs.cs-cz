---
title: Podrobnosti o modulu runtime správy zdrojového kódu | Microsoft Docs
description: Zjistěte, jak je projekt přidán do správy zdrojových kódů, buď když uživatel přidá soubor do projektu ve správě zdrojového kódu nebo prostřednictvím kontroleru automatizace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 213b0096f2bea541fa55840f8f1ea78e8f195cd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905760"
---
# <a name="source-control-runtime-details"></a>Podrobnosti modulu CLR správy zdrojového kódu
Projekt je přidán do správy zdrojového kódu, když uživatel přidá soubor do správy zdrojového kódu nebo prostřednictvím kontroleru automatizace, jako je například Průvodce. Projekt není určen pro sebe samé, že se nachází pod správou zdrojového kódu; podporuje správu zdrojového kódu, ale je nutné do něj přidat ručně.

## <a name="registering-with-a-source-control-package"></a>Registrace do balíčku správy zdrojového kódu
 Když je do správy zdrojového kódu přidán soubor v projektu, prostředí zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> čtyři neprůhledné řetězce, které jsou používány systémem správy zdrojového kódu jako soubory cookie. Uložte tyto řetězce do souboru projektu. Tyto řetězce by měly být předány zástupnému kódu pro správu zdrojového kódu (součást sady Visual Studio, která spravuje balíčky správy zdrojového kódu) při spuštění typu projektu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Tím se zase načte příslušný balíček správy zdrojových kódů a předá se volání ke své implementaci `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
