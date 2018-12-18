---
title: Model pro balíčky správy zdrojového kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27bac56b862d4a3dfd0495420ee20920801faaae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734138"
---
# <a name="model-for-source-control-packages"></a>Model pro balíčky správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující model představuje příklad implementace ovládacího prvku zdroje. V modelu uvidíte, které musí implementovat rozhraní a prostředí služby, které je nutné volat. Stejně jako všechny služby ve skutečnosti volat metody určité rozhraní, který získáte mimo jiné služby. Aby bylo snazší zjistit, jak se provádí správy zdrojového kódu se identifikují názvy tříd.  
  
 ![SCC&#95;TUP příklady](../../extensibility/internals/media/scc-tup.gif "SCC_TUP –")  
Příklad projektu ve správě zdrojového  
  
## <a name="interfaces"></a>Rozhraní  
 Správy zdrojového kódu můžete implementovat pro vaši nových typů projektů v sadě Visual Studio pomocí seznam rozhraní, které jsou uvedeny v následující tabulce.  
  
|Rozhraní|Použití|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Volá se, projekty a editory před jejich uložit nebo soubory změnu (změny). Toto rozhraní se přistupuje pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> služby.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Je voláno projekty můžete požádat o oprávnění, které chcete přidat, odebrat nebo přejmenovat soubor nebo adresář. Toto rozhraní se také nazývá projekty informovat, že je kompletní prostředí, když se schválené přidat, odebrat nebo přejmenovat akce. Přistupuje se k němu pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> služby.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Každá entita, která registruje upozornění, až projekty přidání, přejmenování nebo odstranění souboru nebo adresáře implementované. Chcete-li zaregistrovat pro oznámení události, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Je voláno projekty k registraci balíčku ovládací prvek zdroje a získat informace o stav správy zdrojových kódů. Toto rozhraní se přistupuje pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> služby.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementovaná tímto projektem reagovat na požadavky řízení zdrojové informace o souborech a získat zdroj nastavení nezbytný pro soubor projektu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)

