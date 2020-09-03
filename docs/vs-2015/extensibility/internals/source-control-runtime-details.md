---
title: Podrobnosti o modulu runtime správy zdrojového kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb52770557fa37a14040b686dcdfbf345a713a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183371"
---
# <a name="source-control-runtime-details"></a>Podrobnosti modulu CLR správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projekt je přidán do správy zdrojového kódu, když uživatel přidá soubor do správy zdrojového kódu nebo prostřednictvím kontroleru automatizace, jako je například Průvodce. Projekt není určen pro sebe samé, že se nachází pod správou zdrojového kódu; podporuje správu zdrojového kódu, ale je nutné do něj přidat ručně.  
  
## <a name="registering-with-a-source-control-package"></a>Registrace do balíčku správy zdrojového kódu  
 Když je do správy zdrojového kódu přidán soubor v projektu, prostředí zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> čtyři neprůhledné řetězce, které jsou používány systémem správy zdrojového kódu jako soubory cookie. Uložte tyto řetězce do souboru projektu. Tyto řetězce by měly být předány zástupnému kódu pro správu zdrojového kódu (součást sady Visual Studio, která spravuje balíčky správy zdrojového kódu) při spuštění typu projektu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Tím se zase načte příslušný balíček správy zdrojových kódů a předá se volání ke své implementaci `IVsSccManager2::RegisterSccProject` .  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
