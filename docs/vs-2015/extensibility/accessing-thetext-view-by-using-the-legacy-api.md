---
title: Přístup k zobrazení theText pomocí starší verze rozhraní API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184956"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Přístup k textovému zobrazení pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Textové zobrazení je prezentace textu, který je uložený v textové vyrovnávací paměti. K zobrazení textu můžete přistupovat pomocí starší verze rozhraní API, jak je znázorněno v následující části.  
  
## <a name="text-view-object"></a>Objekt zobrazení textu  
 Každé zobrazení je přidruženo k vlastnímu textové vyrovnávací paměti a zobrazení je okno s daty ve vyrovnávací paměti. Následující diagram znázorňuje klíčová rozhraní objektu zobrazení textu, který je reprezentován <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Objekt zobrazení textu sady Visual Studio](../extensibility/media/vstextview.gif "vstextview")  
Objekt zobrazení textu  
  
 Zobrazení je způsob, jak prezentovat text ve vyrovnávací paměti. Obsahuje funkce, jako je zalamování řádků a sbalení, takže to, co vidíte v zobrazení, není přesným znázorněním textu ve vyrovnávací paměti.  
  
 Zobrazení umožňuje jiným službám nebo procesům zachytit příchozí příkazy a reagovat na ně před tím, než zobrazení na nich bude pracovat. Nejběžnější službou je to, že se jedná o jazykovou službu. Služba jazyka může například potřebovat k zachycení příkazu pro klávesu ENTER, aby poskytovala vlastní odsazení chování nebo tipy nástrojů.  
  
## <a name="adding-functionality-to-the-text-view"></a>Přidání funkcí do textového zobrazení  
 Můžete přizpůsobit chování zobrazení textu zpracováním specifických kláves. Pro zachycení klávesových úhozů implementujete <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> u svého objektu a zadáte cíl příkazu ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) pro monitorování a zachycení příkazů.  
  
 Textové zobrazení používá sekvenční architekturu pro filtry příkazů. Nové filtry příkazů ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objekty) jsou přidány do sekvence voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody.  
  
 Oznámení o události pro textové zobrazení je k dispozici pomocí `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` rozhraní. Implementací tohoto rozhraní do objektu klienta získáte oznámení o změnách v zobrazení text. Zpřístupní toto rozhraní pro zobrazení textu pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> rozhraní v zobrazení text pro příjem oznámení o změnách ze zobrazení.  
  
## <a name="see-also"></a>Viz také  
 [Změna nastavení zobrazení pomocí starší verze rozhraní API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Použití textového správce k monitorování globálního nastavení](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
