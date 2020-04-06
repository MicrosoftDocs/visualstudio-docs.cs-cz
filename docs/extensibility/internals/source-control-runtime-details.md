---
title: Podrobnosti o běhu za spouštění zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705043"
---
# <a name="source-control-runtime-details"></a>Podrobnosti modulu CLR správy zdrojového kódu
Projekt je přidán do správy zdrojového kódu, když uživatel přidá soubor v projektu do správy zdrojového kódu nebo prostřednictvím řadiče automatizace, jako je například průvodce. Projekt nespecifikuje pro sebe, že je pod shodou zdrojového kódu; podporuje správě zdrojového kódu, ale musí být do ní přidána ručně.

## <a name="registering-with-a-source-control-package"></a>Registrace pomocí balíčku správy zdrojového kódu
 Při přidání souboru v projektu do správy <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> zdrojového kódu prostředí volá poskytnout čtyři neprůhledné řetězce, které se používají jako soubory cookie systémem správy zdrojového kódu. Uložte tyto řetězce do souboru projektu. Tyto řetězce by měly být předány do kódu se zakázaným inzerováním zdrojového kódu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>(součást sady Visual Studio, která spravuje balíčky správy zdrojového kódu) při spuštění typu projektu voláním . To zase načte příslušný balíček správy zdrojového kódu `IVsSccManager2::RegisterSccProject`a předá volání jeho implementaci .

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
