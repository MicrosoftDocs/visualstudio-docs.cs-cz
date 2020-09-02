---
title: 'Postupy: poskytnutí kontextu pro editory | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858299"
---
# <a name="how-to-provide-context-for-editors"></a>Postupy: Poskytnutí kontextu pro editory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pro Editor je kontext aktivní pouze v případě, že má Editor fokus nebo byl zaostřený před přesunutím fokusu do okna nástroje. Kontext pro Editor můžete zadat následujícím způsobem:  
  
1. Vytvořte kontejner kontextu.  
  
2. Publikovat kontextový vak do identifikátoru elementu výběru (SEID).  
  
3. Udržujte kontext v kontejneru.  
  
   Tyto úlohy jsou pokryté následujícími postupy. Další informace o tom, jak kontext poskytnout, najdete v části **robustní programování** dále v tomto tématu.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Vytvoření balíčku kontextu pro Editor nebo návrháře  
  
1. Zavolejte `QueryService` na <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> rozhraní pro <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> službu.  
  
     Vrátí se ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> rozhraní.  
  
2. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> metodu pro vytvoření nového kontextu nebo vaku podkontextu.  
  
     Vrátí se ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> rozhraní.  
  
3. Voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> metody přidejte atributy, klíčová slova pro vyhledávání nebo klíčová slova F1 do kontejneru kontextu nebo podkontextu.  
  
4. Pokud vytváříte vaku pro dílčí kontext, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> metodu pro propojení vaku podkontextu s nadřazeným kontejnerem kontextu.  
  
5. Volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> se, aby se zobrazilo oznámení, když se chystá aktualizace okna **dynamického pomocníka** .  
  
     Má-li okno **dynamické** aktualizace zavolat váš editor, když je připraven k aktualizaci, získáte možnost zpozdit změnu kontextu, dokud nedojde k aktualizaci. To může zvýšit výkon, protože umožňuje zpozdit spuštění časově náročných algoritmů, dokud nebude k dispozici systémový čas nečinnosti.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Publikování kontextu balíčku do SEID  
  
1. Zavolejte `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> službu a vraťte ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> rozhraní.  
  
2. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> , zadáním identifikátoru prvku ( `elementid` parametr) SEID_UserContext, abyste označili, že předáváte kontext globální úrovni.  
  
3. Když editor nebo Návrhář přestanou být aktivní, hodnoty ve svém <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objektu budou šířeny do globálního výběru. Tento proces je nutné provést pouze jednou pro každou relaci a následně uložit ukazatel na globální kontext vytvořený při volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> .  
  
### <a name="to-maintain-the-context-bag"></a>Údržba balíčku kontextu  
  
1. Implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> zajistěte, aby **dynamické okno Help** volalo Editor nebo návrháře před aktualizací.  
  
     Pro každý kontextový kontejner, který se volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> po vytvoření a implementaci balíčku kontextu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> , volá rozhraní IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> aby oznámilo zprostředkovateli kontextu, že se kontextový kontejner aktualizuje. Toto volání můžete použít ke změně atributů a klíčových slov v kontejneru kontextu a v jakýchkoli dílčích kontextech, než dojde k aktualizaci **dynamického okna Help** .  
  
2. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> na kontejner kontextu, aby označoval, že editor nebo Návrhář má nový kontext.  
  
     Když **dynamické okno Help** volá, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> aby označovalo, že se aktualizuje, Editor nebo Návrhář může kontext aktualizovat odpovídajícím způsobem v nadřazeném balíčku kontextu a všech podkontextech v daném čase.  
  
    > [!NOTE]
    > `SetDirty`Příznak je automaticky nastaven na `true` vždy, když je do balíčku kontextu přidáno nebo odebrán kontext. **Dynamické okno Help** volá pouze <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> na kontejner kontextu, pokud `SetDirty` je příznak nastaven na hodnotu `true` . Po aktualizaci se obnoví `false` .  
  
3. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> pro přidání kontextu do aktivní kolekce kontextu nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> pro odebrání kontextu.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud píšete vlastní editor, je nutné dokončit všechny tři postupy v tomto tématu a poskytnout tak kontext pro Editor.  
  
> [!NOTE]
> Chcete-li správně aktivovat editor nebo okno návrháře a zajistit, aby bylo směrování příkazu správně aktualizováno, je nutné zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> na součást, aby se aktivovala okna.  
  
 SEID je kolekce vlastností, které se mění v závislosti na výběru. Informace SEID jsou k dispozici prostřednictvím globálního výběru. Globální výběr je zapojený do událostí aktivovaných <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> rozhraním a má seznam všeho, co je vybráno (aktuální editor, aktuální okno nástrojů, aktuální hierarchie atd.).  
  
 V případě editorů a návrhářů, ve kterých se může kontext změnit vždy, když se kurzor přesune do slova, je neefektivní průběžně aktualizovat kontextový kontejner. Chcete-li aktualizovat efektivnější pokaždé, když zjistíte pohyb kurzoru v okně editoru nebo návrháře, můžete zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> . Díky tomu můžete uchovávat změny kontextu, dokud nedojde k nečinnosti a kontextová služba IDE odesílá oznámení do editoru nebo návrháře, že se aktualizuje okno **dynamické** aktualizace. Tento přístup se používá v postupu udržování balíčku kontextu v tomto tématu.  
  
 Po poskytnutí kontextu pro aktivity v editoru nebo Návrháři byste měli zadat konkrétní klíčové slovo F1, které uživatelům umožní získat nápovědu pro Editor nebo návrháře samotného.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
