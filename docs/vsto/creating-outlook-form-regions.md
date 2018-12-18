---
title: Vytváření oblastí formulářů aplikace Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5d4aed381841d5f88209aefdcff641a2a821f01
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673078"
---
# <a name="create-outlook-form-regions"></a>Vytváření oblastí formulářů aplikace Outlook
  Oblasti formuláře můžete použít k přizpůsobení formulářů aplikace Microsoft Office Outlook. Visual Studio poskytuje pokročilé nástroje, které usnadňují návrh, vývoj a ladění oblasti formuláře.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Toto téma poskytuje následující informace:  
  
-   [Mezi výhody používání oblasti formuláře](#Enhance)  
  
-   [Přidání oblasti formuláře Outlooku do projektu](#Adding)  
  
-   [Použití návrhářem oblasti formuláře](#UsingFormRegionDesigner)  
  
-   [Použijte oblast formuláře navržené v aplikaci Outlook](#UsingFormRegionDesignedOutlook)  
  
-   [Přidání vlastního kódu pro oblasti formuláře](#AddingCustomCode)  
  
-   [Sestavení projektu](#Building)  
  
-   [Ladění oblasti formuláře](#Debugging)  
  
-   [Nasazení oblasti formuláře](#Deploying)  
  
##  <a name="Enhance"></a> Mezi výhody používání oblasti formuláře  
 Oblasti formuláře nabízí mnoho vylepšení v tradičních vývojových formulářů aplikace Outlook:  
  
- Přizpůsobení výchozí stránku jakékoli běžného formuláře.  
  
- Přidáte do jakékoli formy standardu až 12 další stránky.  
  
- Nahraďte nebo vylepšit jakékoli běžného formuláře.  
  
- Zobrazit vlastní uživatelské rozhraní v podokně čtení a kontroly.  
  
  Další informace najdete v tématu [přizpůsobit stránky formuláře a oblasti formulářů](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).  
  
##  <a name="Adding"></a> Přidání oblasti formuláře Outlooku do projektu  
 Můžete použít **novou oblast formuláře Outlooku** Průvodce navrhnout novou oblast formuláře nebo import oblasti formuláře, která je navržená v Outlooku. Také pokud máte oblasti formuláře, který jste použili v jiném projektu doplňku VSTO pro Outlook, můžete využít vaše stávající oblast formuláře.  
  
###  <a name="CreatingFormRegion"></a> Vytvořit novou oblast formuláře s použitím Průvodce  
 Chcete-li vytvořit oblasti formuláře, přidejte **oblast formuláře Outlooku** položky do projektu doplňku VSTO v Outlooku. Tím se spustí **novou oblast formuláře Outlooku** průvodce.  
  
 Pomocí průvodce k označení, zda chcete navrhnout novou oblast formuláře nebo import oblasti formuláře, která je navržená v Outlooku. Další informace o navrhování novou oblast formuláře zobrazit [použít návrhářem oblasti formuláře](#UsingFormRegionDesigner). Další informace o používání oblasti formuláře navržené v aplikaci Outlook, naleznete v tématu [Import oblasti formuláře navržené v aplikaci Outlook](#UsingFormRegionDesignedOutlook).  
  
 Chcete-li určit typ oblasti formuláře, kterou chcete vytvořit pomocí průvodce. Následující tabulka popisuje každý typ oblasti formuláře.  
  
|Typ oblasti|Popis|  
|-----------------|-----------------|  
|Samostatné|Přidává oblast formuláře na novou stránku ve formuláři Outlooku.|  
|Přiléhající|Připojí oblasti formuláře do dolní části stránky výchozího formuláře aplikace Outlook.|  
|Nahrazení|Přidává oblast formuláře na novou stránku, která nahradí výchozí stránku formuláře aplikace Outlook.|  
|Nahradit všechno|Nahradí celý formulář Outlook oblasti formuláře.|  
  
 Průvodce můžete použít také k určení podmínek, zobrazení a vyberte typ pro formulář k rozšíření. Další informace najdete v tématu [postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Možnosti, které provedete v Průvodci vliv na možnosti, které jsou k dispozici na jiných stránkách průvodce. Pokud vyberete třeba **sousedící** nebo **samostatné** v **vytvořit novou oblast formuláře Outlooku** stránky, pak bude **Title** a **Popis** pole jsou k dispozici v **zadání popisného textu a výběr předvoleb zobrazení** stránky. Je to proto, že aplikace Outlook nepoužívá tato pole poznat sousední nebo samostatné oblasti formuláře.  
  
#### <a name="form-region-files"></a>Soubory oblasti formuláře  
 Po dokončení **novou oblast formuláře Outlooku** Průvodce aplikace Visual Studio automaticky přidá následující soubory do projektu:  
  
-   Soubor kódu oblasti formuláře. Tento soubor má název, který zadáte pro **oblast formuláře Outlooku** položky v **přidat novou položku** dialogové okno. Přidejte kód pro zpracování události oblasti formuláře do tohoto souboru.  
  
-   Soubor návrháře kódu oblasti formuláře. Tento soubor obsahuje kód generovaný návrhářem oblasti formuláře a neměl by být upravován přímo.  
  
-   Úložiště formulářů Outlooku (*.ofs*) soubor.  
  
    > [!NOTE]  
    >  Tento soubor je přidat do projektu pouze pokud import oblasti formuláře, která je navržená v Outlooku.  
  
#### <a name="form-region-factory-class"></a>Třída objekt pro vytváření oblasti formuláře  
 Soubor kódu oblasti formuláře obsahuje částečné třídy, která implementuje <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> rozhraní. Toto je třída objekt pro vytváření oblasti formuláře. Třída objekt pro vytváření oblasti formuláře zodpovídá za vytvoření nové instance oblasti formuláře.  
  
 Tuto třídu můžete najít tak, že rozbalíte **objekt pro vytváření oblasti formuláře** oblasti.  
  
 **Novou oblast formuláře Outlooku** průvodce přidá do této třídy, která zadejte interní název této oblasti formuláře a tříd zpráv, které se oblast formuláře zobrazit atributy. Tyto atributy můžete upravit ručně po přidání souboru do projektu.  
  
 Většina tříd objekt pro vytváření oblasti formuláře je implementované v souboru návrháře oblasti formuláře. Ale `FormRegionInitializing` obslužná rutina události je přístupný v souboru kódu oblasti formuláře. Tuto obslužnou rutinu události můžete použít k určení, zda by měla oblast formuláře zobrazit aplikace Outlook. Další informace najdete v tématu [zpracování událostí oblasti formuláře](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a> Přidat existující oblasti formuláře do projektu  
 Pokud máte oblasti formuláře Outlooku, který jste použili v jiném projektu aplikace Outlook, jej můžete znovu použít v aktuálním projektu doplňku VSTO pro Outlook s použitím **přidat existující položku** dialogové okno.  
  
 Existující oblasti formuláře musí mít soubor s kódem (*.vb* nebo *.cs*); nelze přidat úložiště formulářů Outlooku (*.ofs*) souborů pomocí **přidat existující položku** dialogové okno. Můžete však vytvořit novou oblast formuláře importováním soubor úložiště formulářů Outlooku. Další informace najdete v tématu [postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a> Použití návrhářem oblasti formuláře  
 Návrhářem oblasti formuláře umožňuje navrhovat rozložení a vzhled oblasti formuláře. Přetáhněte ovládací prvky spravovaného na plochu návrháře, poklepejte na ovládací prvky pro otevření obslužné rutiny událostí a nastavte vlastnosti **vlastnosti** okna.  
  
> [!NOTE]  
>  Můžete najít vlastnosti, které ovlivňují způsob, jak se oblast formuláře zobrazí v aplikaci Outlook pod **Manifest** uzlu **vlastnosti** okno.  
  
 Návrhářem oblasti formuláře je k dispozici pouze v případě, že vyberete **navrhnout novou oblast formuláře** v **vyberte způsob vytvoření oblasti formuláře** stránku **novou oblast formuláře Outlooku** Průvodce.  
  
 Existují tři způsoby, jak otevřít návrhářem oblasti formuláře:  
  
- V **Průzkumníka řešení**, poklikejte na soubor kódu oblasti formuláře.  
  
- V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor kódu oblasti formuláře a potom klikněte na tlačítko **Návrhář zobrazení**.  
  
- V **Průzkumníka řešení**, vyberte soubor kódu oblasti formuláře a potom na **zobrazení** nabídky, klikněte na tlačítko **návrháře**.  
  
  Návrhář podporuje oblasti formuláře pouze spravovaných ovládacích prvků. Nelze přidat nativní ovládací prvky aplikace Outlook.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Import oblasti formuláře navržené v aplikaci Outlook  
 Při návrhu v Outlooku, můžete přidat nativní ovládací prvky aplikace Outlook na oblast formuláře. Nativní ovládací prvky aplikace Outlook umožňují svázat s daty aplikace Outlook v době návrhu. Spravované ovládací prvky přidat nebo změnit návrh oblasti formuláře nelze však potom použít návrhářem oblasti formuláře.  
  
 Můžete importovat oblasti formuláře do projektu doplňku VSTO pro Outlook v **novou oblast formuláře Outlooku** průvodce. Na **vyberte způsob vytvoření oblasti formuláře** stránce **naimportovat soubor úložiště formulářů Outlooku (.ofs)**. Můžete pak přejděte do umístění souboru úložiště formulářů Outlooku (*.ofs*) soubor. (Aplikace outlook ukládá oblasti formuláře jako *.ofs* souborů.)  
  
 **Novou oblast formuláře Outlooku** Průvodce kopií *.ofs* soubor do adresáře projektu a přidá ovládací prvek odkazů na soubor návrháře oblasti formuláře. Potom můžete zpracovat události ovládacího prvku v souboru kódu oblasti formuláře.  
  
 Zpracování událostí v projektu jazyka Visual Basic, vyberte událost ze seznamu Metoda název v horní části stránky editoru kódu.  
  
 Zpracování událostí v C# projektu, přihlášení k odběru událostí ovládacího prvku v <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> metody. Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události &#40;C&#35; programováním&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).  
  
 Můžete změnit vlastnosti oblasti formuláře v `InitializeManifest` metoda třídy objekt pro vytváření oblasti formuláře.  
  
> [!NOTE]  
>  Import oblasti formuláře, musí být pracujete v projektu, který cílí stejnou verzi aplikace Outlook, kterou jste nainstalovali na vývojovém počítači. Například pokud máte nainstalovanou aplikaci Outlook 2010, import formuláře oblasti se pouze pracovní v projektu bylo vytvořeno s použitím **doplňku aplikace Outlook 2010** šablony projektu.  
  
### <a name="update-an-imported-form-regions-design"></a>Aktualizovat na oblast formuláře importované návrhu  
 Můžete přidat, odebrat nebo změnit ovládacích prvků na oblast formuláře. Než to uděláte, zálohujte veškerý kód, který jste přidali do souboru kódu oblasti formuláře. Pak otevřete *.ofs* souboru v aplikaci Outlook, upravit oblast formuláře a následně změny uložte. Použití **novou oblast formuláře Outlooku** průvodce importujte upravené *.ofs* souboru. Potom můžete vložit kód do souboru kódu novou oblast formuláře.  
  
##  <a name="AddingCustomCode"></a> Přidání vlastního kódu pro oblasti formuláře  
 <xref:Microsoft.Office.Tools.Outlook> Obor názvů poskytuje přístup k tříd, které představují oblasti formuláře, který zobrazí oblasti formuláře položky aplikace Outlook a dalších užitečných položek. **Oblast formuláře Outlooku** položek automaticky přidá odkaz na toto sestavení v projektu a vloží odpovídající **pomocí** nebo **importy** příkazu v horní části soubor kódu oblasti formuláře.  
  
 Můžete použít třídy, metody a vlastnosti v `Microsoft.Office.Interop.Outlook` obor názvů pro provádění většiny programování úkolů Outlooku. Další informace o modelu objektů aplikace Outlook, naleznete v tématu [přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md). Příklady typické úlohy, které využít model objektů aplikace Outlook, naleznete v tématu [řešení pro aplikaci Outlook](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a> Zpracování událostí oblasti formuláře  
 **Oblast formuláře Outlooku** položek automaticky přidá následující obslužné rutiny tři události do souboru kódu oblasti formuláře.  
  
|Událost|Popis|  
|-----------|-----------------|  
|FormRegionInitializing|Proběhne před inicializací oblasti formuláře. Můžete zkontrolovat podmínky v této obslužné rutiny události k určení, zda by měla oblast formuláře zobrazit aplikace Outlook. Další informace najdete v tématu [postupy: zabránění Outlook ze zobrazení oblasti formuláře](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Vyvolá se po vytvoření instance oblasti formuláře, ale před zobrazením této oblasti.|  
|FormRegionClosed|Vyvolá se před uzavřením oblasti formuláře.|  
  
##  <a name="Building"></a> Sestavení projektu  
 Když vytvoříte projekt doplňku VSTO pro Outlook, který obsahuje oblasti formuláře, Visual Studio přidá do registru následující informace:  
  
- Klíč pro každou třídu zpráv, který je přidružený jeden nebo více oblastí formulářů.  
  
- Záznam pro každou oblast formuláře a přidruženou hodnotu, která představuje název doplňku VSTO v Outlooku.  
  
  Aplikace Outlook používá tyto informace načíst oblasti formuláře.  
  
##  <a name="Debugging"></a> Ladění oblasti formuláře  
 Můžete ladit VSTO pro Outlook doplněk, který obsahuje oblasti formuláře, stejně jako by ladění jiných [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty. Při spuštění [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicího programu sady Visual Studio automaticky spustí aplikaci Outlook.  
  
 Chcete-li zobrazit oblast formuláře, je nutné otevřít příslušnou položku aplikace Outlook. Například pokud sousední oblasti formuláře je přidán do dolní části položky pošty, otevřete položku e-mailu.  
  
##  <a name="Deploying"></a> Nasazení oblasti formuláře  
 Oblasti formuláře se automaticky nasadí se přidružené aplikaci Outlook doplňku VSTO. Proto není muset provádět žádné zvláštní úkoly nasazení oblasti formuláře. Další informace o nasazení doplňků VSTO najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Poskytuje informace, které vám může pomoct optimalizovat vaše oblastí formulářů a vyhněte se potenciální problémy.|  
|[Postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Ukazuje postup vytvoření oblasti formuláře rozšířit standardní nebo vlastní formulář aplikace Microsoft Office Outlook s použitím **novou oblast formuláře Outlooku** průvodce.|  
|[Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Vysvětluje, jak určit oblast formuláře zobrazit podle přidružení oblasti formuláře k třídě zpráv každé položky, položky, které aplikace Microsoft Office Outlook.|  
|[Návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md)|Ukazuje, jak navrhovat vlastní formulář regionu, který se zobrazí v okně Inspektor kontaktní položky na novou stránku.|  
|[Návod: Importujte oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Ukazuje, jak návrh oblasti formuláře v aplikaci Microsoft Office Outlook a pak pomocí import oblasti formuláře do projektu doplňku VSTO pro Outlook **novou oblast formuláře Outlooku** průvodce.|  
|[Přístup k oblasti formuláře za běhu](../vsto/accessing-a-form-region-at-run-time.md)|Popisuje, jak napsat kód pro zobrazení skrytí nebo úpravy ovládacích prvků na oblast formuláře a povolit uživatelům spustit kód z jiných oblastí ve vašem projektu pomocí `Globals` třídy.|  
|[Postupy: zabránění zobrazení oblasti formuláře Outlooku](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Ukazuje, jak aplikace Microsoft Office Outlook zabránění zobrazení oblasti formuláře pro určité položky.|  
|Ukazuje, jak pro přístup k položce Outlooku, ve kterém se zobrazí oblasti formuláře.|  
|[Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Popisuje, jak povolit uživatelům reagovat na položky aplikace Outlook.|  
  
