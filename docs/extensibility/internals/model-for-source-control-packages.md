---
title: Model pro balíčky správy zdrojového kódu | Microsoft Docs
description: Tento model představuje implementaci správy zdrojového kódu. Článek ukazuje názvy tříd, aby bylo snazší zjistit, jak se provádí Správa zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4e437afdfa0d3de03da6814e221840cbd0763fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063198"
---
# <a name="model-for-source-control-packages"></a>Model pro balíčky správy zdrojového kódu
Následující model představuje příklad implementace správy zdrojového kódu. V modelu vidíte rozhraní, která je nutné implementovat, a služby prostředí, které je třeba volat. Stejně jako všechny služby skutečně voláte metody konkrétního rozhraní, které obdržíte prostřednictvím služby. Názvy tříd jsou identifikovány, aby bylo snazší zjistit, jak se provádí Správa zdrojového kódu.

 ![Příklady SCC&#95;instalační](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Příklad projektu správy zdrojového kódu

## <a name="interfaces"></a>Rozhraní
 Můžete implementovat správu zdrojového kódu pro nové typy projektů v aplikaci Visual Studio pomocí seznamu rozhraní, která jsou uvedena v následující tabulce.

|Rozhraní|Použití|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Volá se projekty a editory před uložením nebo změnou (nezměněného) souborů. K tomuto rozhraní se používá <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> služba.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Voláno projekty k vyžádání oprávnění k přidání, odebrání nebo přejmenování souboru nebo adresáře. Toto rozhraní je také voláno projekty k informování prostředí, když je dokončena schválená akce přidání, odebrání nebo přejmenování. Je k ní přistupovaná pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> služby.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementováno libovolnou entitou, která se zaregistruje na oznámení, když projekty přidají, přejmenují nebo odeberou soubor nebo adresář. Chcete-li se zaregistrovat k oznámení události, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Volá se projekty k registraci do balíčku správy zdrojového kódu a k získání informací o stavu správy zdrojového kódu. K tomuto rozhraní se používá <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> služba.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementováno projektem pro reakci na požadavky na správu zdrojového kódu pro informace o souborech a k získání nastavení správy zdrojového kódu, které jsou požadovány pro soubor projektu.|

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
