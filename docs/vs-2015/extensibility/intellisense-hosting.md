---
title: Hostování IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203906"
---
# <a name="intellisense-hosting"></a>Hostování technologie IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio umožňuje hostování IntelliSense. Hostování IntellSense vám umožňuje poskytovat IntelliSense pro kód, který není hostovaný v textovém editoru sady Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Využití hostování IntelliSense  
 Jakýkoli kód, který má přístup k sadě dokončení a textové vyrovnávací paměti, může v sadě Visual Studio získat okna IntelliSense z libovolného místa v uživatelském rozhraní (UI). Příklady scénářů tohoto typu jsou dokončovány v okně **kukátka** nebo v poli Podmínka okna vlastností zarážek.  
  
### <a name="implementation-interfaces"></a>Rozhraní implementace  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Jakékoli komponenty uživatelského rozhraní, která je hostitelem překryvných oken technologie IntelliSense, musí podporovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> rozhraní. Výchozí zobrazení textu editoru základní verze zahrnuje implementaci uložených <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> rozhraní, která zachovává aktuální funkce technologie IntelliSense. Ve většině případů metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> rozhraní reprezentují podmnožinu toho, co je implementováno na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní. Podmnožina zahrnuje zpracování uživatelského rozhraní IntelliSense, manipulaci se blikajícím kurzorem a výběr a jednoduchou funkci nahrazení textu. Kromě toho <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> rozhraní umožňuje samostatné IntelliSense "Subject" a "Context", aby bylo možné technologii IntelliSense poskytnout pro předměty, které přímo neexistují v textové vyrovnávací paměti, která je používána pro kontext.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>Zprostředkovatel rozhraní musí implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> metodu, která umožňuje klientovi určit, jaký typ funkcí technologie IntelliSense podporuje hostitel.  
  
 Příznaky hostitele definované v [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)jsou shrnuty níže.  
  
|Příznak hostitele IntelliSense|Popis|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Nastavením tohoto příznaku znamená, že kontextová vyrovnávací paměť je jen pro čtení a úprava probíhá pouze v rámci textu předmětu.|  
|IHF_NOSEPERATESUBJECT|Nastavením tohoto příznaku znamená, že není k dispozici žádný samostatný předmět technologie IntelliSense. Předmět existuje v mezipaměti kontextu, například v tradičním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> systému technologie IntelliSense.|  
|IHF_SINGLELINESUBJECT|Nastavením tohoto příznaku znamená, že subjekt nebude schopen s více řádky, jako je například v případě úpravy na jednom řádku v okně **kukátko** .|  
|IHF_FORCECOMMITTOCONTEXT|Pokud je tento příznak nastaven a je třeba aktualizovat kontextovou vyrovnávací paměť, hostitel povolí, aby byl příznak jen pro čtení v kontextu vyrovnávací paměti ignorován a aby bylo možné pokračovat v úpravách.|  
|IHF_OVERTYPE|Úpravy (v předmětu nebo kontextu) by se měly provádět v režimu přepisování.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost. BeforeCompletorCommit a IVsIntellisenseHost. AfterCompletorCommit  
 Tyto metody zpětného volání jsou volány oknem dokončení před a po potvrzení textu, aby bylo možné povolit předběžné zpracování a následné zpracování.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>Rozhraní je spoluvytvořená verze standardního okna dokončování, které je používáno integrovaným vývojovým prostředím (IDE). Jakékoli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> rozhraní může pomocí tohoto rozhraní completor rychle implementovat technologii IntelliSense.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
