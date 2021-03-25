---
title: Podrobnosti o modulu runtime správy zdrojového kódu | Microsoft Docs
description: Zjistěte, jak je projekt přidán do správy zdrojových kódů, buď když uživatel přidá soubor do projektu ve správě zdrojového kódu nebo prostřednictvím kontroleru automatizace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a25a9c29c828e1d5e70d143ccd3582dc4ec6f48
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064212"
---
# <a name="source-control-runtime-details"></a>Podrobnosti modulu CLR správy zdrojového kódu
Projekt je přidán do správy zdrojového kódu, když uživatel přidá soubor do správy zdrojového kódu nebo prostřednictvím kontroleru automatizace, jako je například Průvodce. Projekt není určen pro sebe samé, že se nachází pod správou zdrojového kódu; podporuje správu zdrojového kódu, ale je nutné do něj přidat ručně.

## <a name="registering-with-a-source-control-package"></a>Registrace do balíčku správy zdrojového kódu
 Když je do správy zdrojového kódu přidán soubor v projektu, prostředí zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> čtyři neprůhledné řetězce, které jsou používány systémem správy zdrojového kódu jako soubory cookie. Uložte tyto řetězce do souboru projektu. Tyto řetězce by měly být předány zástupnému kódu pro správu zdrojového kódu (součást sady Visual Studio, která spravuje balíčky správy zdrojového kódu) při spuštění typu projektu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Tím se zase načte příslušný balíček správy zdrojových kódů a předá se volání ke své implementaci `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
