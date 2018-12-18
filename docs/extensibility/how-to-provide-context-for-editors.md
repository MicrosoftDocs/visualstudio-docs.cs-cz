---
title: 'Postupy: Zadání kontextu editory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 848778506bdea1b7bf61b6a94a1fb14908a7b930
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908911"
---
# <a name="how-to-provide-context-for-editors"></a>Postupy: zadání editory kontextu
Pro editor kontext je aktivní, pouze v případě, že je editor má právě fokus, nebo má fokus, bezprostředně před byl přesunut fokus panelu nástrojů. Můžete zadat kontextu editoru provedením následujících úloh:  
  
1. Vytvořte kontejner kontextu.  
  
2. Publikujte místní kontejner identifikátor elementu výběru (SEID).  
  
3. Udržujte kontextu v kontejneru.  
  
   Tyto úlohy se vztahují následující postupy. Další informace o poskytnutí kontextu najdete v tématu **robustní programování** dále v tomto článku.  
  
## <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Chcete-li vytvořit kontejner kontextu editoru nebo návrháře  
  
1.  Volání `QueryService` na vaše <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> služby.  
  
     Ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> rozhraní se vrátí.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> metodu pro vytvoření nového kontejneru kontextu nebo kontext.  
  
     Ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> rozhraní se vrátí.  
  
3.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> způsob, jak přidat atributy, klíčová slova pro vyhledávání, nebo **F1** klíčových slov pro kontejner objektů a dat kontextu nebo kontext.  
  
4.  Pokud vytvoříte kontejner kontext, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> metoda propojení kontejner kontext do nadřazené místní kontejner objektů a dat.  
  
5.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> pro příjem oznámení při **dynamická Nápověda** okna je aktualizovat.  
  
     Máte **dynamická Nápověda** volání okno editoru až to bude hotové, chcete-li aktualizovat vám dává příležitost pro odložené změny kontextu, až proběhne aktualizace. Tím lze vylepšit výkon, protože umožňuje zpoždění spuštění časově náročné algoritmy, dokud nečinnost systému je k dispozici.  
  
## <a name="to-publish-the-context-bag-to-the-seid"></a>Publikovat SEID kontextu kontejneru  
  
1.  Volání `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> služby a vrátí ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> rozhraní.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, určující identifikátor elementu (`elementid` parametr) hodnotu SEID_UserContext k označení, že předáváte kontext na globální úrovni.  
  
3.  Když stane aktivním editoru nebo návrháře, hodnot v jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objektu se rozšíří do globálního výběru. Je potřeba jenom to provést jednou na relaci a potom uložte ukazatele na globální kontext vytvoří, když jste volali <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
## <a name="to-maintain-the-context-bag"></a>Udržovat kontextu kontejneru  
  
1.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> zajistit, aby **dynamická Nápověda** volá okno editoru nebo návrháře předtím, než se aktualizuje.  
  
     Pro každý místní kontejner objektů a dat, které se nazývá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> po vytvoření kontejneru objektů a dat kontextu a implementoval <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, volání IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> upozornit poskytovatele kontextu zaktualizuje kontejner kontextu. Chcete-li změnit atributy a klíčová slova v kontejneru a kontextu a jakékoli kontext kontejnery objektů a dat, než můžete použít toto volání **dynamická Nápověda** Probíhá aktualizace okna.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> na kontejner objektů a dat kontext k označení, že editoru nebo návrháře má nový kontext.  
  
     Když **dynamická Nápověda** volání okno <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> k označení, že se aktualizuje, editoru nebo návrháře v tu chvíli můžete aktualizovat kontext odpovídajícím způsobem pro nadřazené místní kontejner objektů a dat a všechny kontejnery objektů a dat kontext.  
  
    > [!NOTE]
    >  `SetDirty` Příznak je automaticky nastaven na `true` vždy, když přidá nebo odebere z kontejneru objektů a dat rámci kontextu. **Dynamická Nápověda** okno jen volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> na kontejner a kontext dat pokud `SetDirty` příznak je nastaven na `true`. Resetuje na `false` po aktualizaci.  
  
3.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> k přidání kontextu do kolekce aktivní kontext nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> odebrat kontext.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud vytváříte vlastní editor, je třeba provést všechny tři postupy v tomto článku poskytují kontext v editoru.  
  
> [!NOTE]
>  Správně aktivovat editoru nebo návrháře oken a ujistěte se, že směrování příkazů aktualizaci správně, je nutné volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> komponenty k němu okno fokus.  
  
 SEID je kolekce vlastností, které se mění v závislosti na výběru. SEID informace jsou k dispozici prostřednictvím globálního výběru. Do události aktivované přes drátové sítě globální výběr <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> rozhraní, a seznam všechno, co se vybral (aktuální editor, aktuální okno nástroje, aktuální hierarchií a tak dále).  
  
 Pro editorů a návrhářů v daném kontextu může změnit pokaždé, když kurzor se přesune do slova, je neefektivní neustále aktualizovat kontejner kontextu. Chcete-li aktualizaci efektivnější kdykoli zjistit kurzoru přesouvat v rámci editoru nebo návrháře oken, můžete volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Díky tomu se můžete k uložení změny kontextu, dokud není čas nečinnosti a místní služba integrované vývojové prostředí odešle oznámení do editoru nebo návrháře, který **dynamická Nápověda** okno se aktualizuje. Tento přístup se používá v **udržovat místní kontejner** postup v tomto článku.  
  
 Po zadání kontext pro aktivity v rámci editoru nebo návrháře, měli byste zadat konkrétní **F1** – klíčové slovo, aby uživatelé pro získání nápovědy pro editoru nebo návrháře, samotného.  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>