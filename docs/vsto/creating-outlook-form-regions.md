---
title: Vytvoření oblastí formuláře aplikace Outlook
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8a999ca11427533690628fb92f28e93d22cf0971
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255919"
---
# <a name="create-outlook-form-regions"></a>Vytvoření oblastí formuláře aplikace Outlook
  Oblasti formulářů můžete použít k přizpůsobení systém Microsoft Officech formulářů aplikace Outlook. Visual Studio poskytuje pokročilé nástroje, které usnadňují návrh, vývoj a ladění oblastí formuláře.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Toto téma poskytuje následující informace:

- [Výhody používání oblastí formulářů](#Enhance)

- [Přidání oblasti formuláře Outlooku do projektu](#Adding)

- [Použití návrháře oblasti formuláře](#UsingFormRegionDesigner)

- [Použití oblasti formuláře navržené v aplikaci Outlook](#UsingFormRegionDesignedOutlook)

- [Přidání vlastního kódu do oblasti formuláře](#AddingCustomCode)

- [Sestavení projektu](#Building)

- [Ladění oblasti formuláře](#Debugging)

- [Nasazení oblasti formuláře](#Deploying)

## <a name="Enhance"></a>Výhody používání oblastí formulářů
 Oblasti formulářů nabízejí řadu vylepšení oproti tradičnímu vývoji formulářů Outlook:

- Přizpůsobení výchozí stránky libovolného standardního formuláře.

- Přidejte až 12 dalších stránek do libovolného standardního formuláře.

- Nahraďte nebo Vylepšete všechny standardní formuláře.

- Zobrazit vlastní uživatelské rozhraní v podokně pro čtení a v kontrolorech.

  Další informace najdete v tématu [přizpůsobení stránek formuláře a oblastí formuláře](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).

## <a name="Adding"></a>Přidání oblasti formuláře Outlooku do projektu
 Průvodce vytvořením **nové oblasti formuláře Outlook** můžete použít k návrhu nové oblasti formuláře nebo importu oblasti formuláře, která byla navržena v aplikaci Outlook. Pokud máte oblast formuláře, kterou jste použili v jiném projektu doplňku VSTO pro Outlook, můžete znovu použít stávající oblast formuláře.

### <a name="CreatingFormRegion"></a>Vytvoření nové oblasti formuláře pomocí Průvodce
 Chcete-li vytvořit oblast formuláře, přidejte položku **oblasti formuláře aplikace Outlook** do projektu doplňku aplikace Outlook VSTO. Tím spustíte Průvodce vytvořením **nové oblasti formuláře Outlooku** .

 Průvodce použijte k určení, zda chcete navrhnout novou oblast formuláře nebo importovat oblast formuláře, která byla navržena v aplikaci Outlook. Další informace o návrhu nové oblasti formuláře najdete v tématu [použití návrháře oblasti formuláře](#UsingFormRegionDesigner). Další informace o použití oblasti formuláře navržené v aplikaci Outlook najdete v tématu [import oblasti formuláře navržené v aplikaci Outlook](#UsingFormRegionDesignedOutlook).

 Průvodce použijte k určení typu oblasti formuláře, kterou chcete vytvořit. Následující tabulka popisuje jednotlivé typy oblastí formuláře.

|Typ oblasti|Popis|
|-----------------|-----------------|
|Jednotlivých|Přidá oblast formuláře jako novou stránku do formuláře aplikace Outlook.|
|Přiléhající|Připojí oblast formuláře k dolnímu okraji výchozí stránky formuláře aplikace Outlook.|
|Nahrazení|Přidá oblast formuláře jako novou stránku, která nahradí výchozí stránku formuláře aplikace Outlook.|
|Nahradit vše|Nahradí celý formulář aplikace Outlook oblastmi formuláře.|

 Průvodce můžete také použít k zadání podmínek zobrazení a výběru typu formuláře, který chcete zvětšit. Další informace najdete v tématu [jak: Přidejte oblast formuláře do projektu](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)doplňku pro Outlook.

 Výběry provedené v průvodci ovlivňují možnosti, které jsou k dispozici na dalších stránkách průvodce. Pokud například vyberete možnost **sousedící** nebo **oddělené** na stránce **vytvořit novou oblast formuláře aplikace Outlook** , pole **název** a **Popis** nebudou k dispozici v **popisném textu pro zadání a vyberte zobrazení. Stránka předvolby** Je to proto, že Outlook nepoužívá tato pole, když zobrazuje sousedící nebo oddělené oblasti formuláře.

#### <a name="form-region-files"></a>Soubory oblastí formuláře
 Po dokončení Průvodce vytvořením **nové oblasti formuláře aplikace** Visual Studio automaticky přidá do projektu následující soubory:

- Soubor kódu oblasti formuláře Tento soubor má název, který zadáte pro položku **oblast formuláře Outlook** v dialogovém okně **Přidat novou položku** . Přidejte kód pro zpracování událostí oblasti formuláře do tohoto souboru.

- Soubor s kódem návrháře oblasti formuláře Tento soubor obsahuje kód generovaný návrhářem oblasti formuláře a neměl by být přímo upravován.

- Soubor úložiště formuláře aplikace Outlook ( *. ofs*).

    > [!NOTE]
    > Tento soubor je přidán do projektu pouze v případě, že importujete oblast formuláře, která byla navržena v aplikaci Outlook.

#### <a name="form-region-factory-class"></a>Třída factory oblasti formuláře
 Soubor kódu oblasti formuláře obsahuje částečnou třídu, která implementuje <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> rozhraní. Toto je třída objektu pro vytváření oblastí formuláře. Třída factory oblasti formuláře zodpovídá za vytváření nových instancí oblasti formuláře.

 Tuto třídu můžete najít rozbalením oblasti pro **vytváření oblastí formuláře** .

 Průvodce **vytvořením nové oblasti formuláře Outlooku** přidá do této třídy atributy, které určují interní název oblasti formuláře a třídy zpráv, které zobrazují oblast formuláře. Tyto atributy lze upravit ručně poté, co byl soubor přidán do projektu.

 Většina třídy Factory oblasti formuláře je implementována v souboru návrháře oblasti formuláře. Nicméně obslužná rutina události je vystavena v souboru kódu oblasti formuláře. `FormRegionInitializing` Tuto obslužnou rutinu události můžete použít k určení, zda má aplikace Outlook zobrazit oblast formuláře. Další informace najdete v tématu [zpracování událostí oblasti formuláře](#HandlingFormRegionEvents).

### <a name="AddingExistingFormRegion"></a>Přidání existující oblasti formuláře do projektu
 Pokud máte oblast formuláře Outlooku, kterou jste použili v jiném projektu Outlooku, můžete ji znovu použít v aktuálním projektu doplňku VSTO pro Outlook pomocí dialogového okna **Přidat existující položku** .

 Existující oblast formuláře musí mít soubor kódu ( *. vb* nebo *. cs*); pomocí dialogového okna **Přidat existující položku** nemůžete přidat soubory úložiště formuláře aplikace Outlook ( *. ofs*). Novou oblast formuláře ale můžete vytvořit tak, že naimportujete soubor úložiště formuláře aplikace Outlook. Další informace najdete v tématu [jak: Přidejte oblast formuláře do projektu](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)doplňku pro Outlook.

## <a name="UsingFormRegionDesigner"></a>Použití návrháře oblasti formuláře
 Návrhář oblasti formuláře vám pomůže navrhnout rozložení a vzhled oblasti formuláře. Můžete přetáhnout spravované ovládací prvky na povrch návrháře, dvakrát kliknout na ovládací prvky pro otevření obslužných rutin událostí a nastavit vlastnosti v okně **vlastnosti** .

> [!NOTE]
> Můžete najít vlastnosti, které mají vliv na způsob, jakým se oblast formuláře zobrazuje v aplikaci Outlook pod uzlem **manifest** v okně **vlastnosti** .

 Návrhář oblasti formuláře je k dispozici pouze v případě, že jste vybrali možnost **návrh nové oblasti formuláře** na stránce **Vyberte, jak chcete vytvořit oblast** formuláře v Průvodci vytvořením **oblasti formuláře aplikace Outlook** .

 Existují tři způsoby, jak otevřít Návrhář oblasti formuláře:

- V **Průzkumník řešení**dvakrát klikněte na soubor kódu oblasti formuláře.

- V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor kódu oblasti formuláře a pak klikněte na tlačítko **Návrhář zobrazení**.

- V **Průzkumník řešení**vyberte soubor kódu oblasti formuláře a potom v nabídce **zobrazení** klikněte na **Návrhář**.

  Návrhář oblasti formuláře podporuje pouze spravované ovládací prvky. Nelze přidat nativní ovládací prvky aplikace Outlook.

## <a name="UsingFormRegionDesignedOutlook"></a>Import oblasti formuláře navržené v aplikaci Outlook
 Při návrhu v aplikaci Outlook lze do oblasti formuláře přidat nativní ovládací prvky aplikace Outlook. Nativní ovládací prvky aplikace Outlook umožňují vytvořit vazby na data aplikace Outlook v době návrhu. Pomocí návrháře oblastí formuláře ale nelze přidat spravované ovládací prvky nebo změnit návrh oblasti formuláře.

 Do projektu doplňku VSTO pro Outlook můžete importovat oblasti formulářů pomocí Průvodce vytvořením **nové oblasti formuláře Outlooku** . Na stránce **Vyberte, jak chcete vytvořit oblast formuláře** vyberte možnost **importovat soubor úložiště formuláře aplikace Outlook (. ofs)** . Pak můžete přejít do umístění souboru úložiště formuláře aplikace Outlook ( *. ofs*). (Outlook ukládá oblasti formulářů jako soubory *. ofs* .)

 Průvodce **novou oblastí formuláře Outlooku** zkopíruje soubor *. ofs* do adresáře projektu a přidá odkazy na ovládací prvek do souboru návrháře oblasti formuláře. Pak můžete zpracovat události řízení v souboru kódu oblasti formuláře.

 Chcete-li zpracovávat události v projektu Visual Basic, vyberte událost ze seznamu název metody v horní části editoru kódu.

 Chcete-li zpracovávat události C# v projektu, přihlaste se k <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> odběru řídicích událostí v metodě. Další informace najdete v tématu [jak: Přihlaste se k odběru a &#40;odhlaste&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events)se z Průvodce programováním událostí C&#35; .

 Vlastnosti oblasti formuláře můžete změnit v `InitializeManifest` metodě třídy Factory oblasti formuláře.

> [!NOTE]
> Chcete-li importovat oblast formuláře, je nutné pracovat v projektu, který cílí na stejnou verzi aplikace Outlook, kterou jste nainstalovali do vývojového počítače. Například pokud máte nainstalovanou aplikaci Outlook 2010, import oblasti formuláře bude pracovat pouze v projektu pomocí šablony projektu **doplňku pro aplikaci Outlook 2010** .

### <a name="update-an-imported-form-regions-design"></a>Aktualizace návrhu oblasti importovaného formuláře
 Můžete přidat, odebrat nebo změnit ovládací prvky v oblasti formuláře. Předtím, než to uděláte, zazálohujte veškerý kód, který jste přidali do souboru kódu oblasti formuláře. Pak otevřete soubor *. ofs* v aplikaci Outlook, upravte oblast formuláře a uložte změny. K importu upraveného souboru *. ofs* použijte Průvodce vytvořením **nové oblasti formuláře Outlooku** . Kód pak můžete vložit do nového souboru kódu oblasti formuláře.

## <a name="AddingCustomCode"></a>Přidání vlastního kódu do oblasti formuláře
 <xref:Microsoft.Office.Tools.Outlook> Obor názvů poskytuje přístup ke třídám, které reprezentují oblast formuláře, položku Outlooku, která zobrazuje oblast formuláře, a další užitečné položky. Položka **oblasti formuláře aplikace Outlook** automaticky přidá odkaz na toto sestavení v projektu a vloží příslušný příkaz **using** nebo **Imports** v horní části souboru kódu oblasti formuláře.

 Můžete použít třídy, metody a vlastnosti v `Microsoft.Office.Interop.Outlook` oboru názvů k provádění většiny úloh programování v aplikaci Outlook. Další informace o modelu objektu aplikace Outlook najdete v tématu [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md). Příklady typických úloh, které využívají objektový model aplikace Outlook, najdete v tématu [řešení aplikace Outlook](../vsto/outlook-solutions.md).

### <a name="HandlingFormRegionEvents"></a>Zpracování událostí oblasti formuláře
 Položka **oblasti formuláře aplikace Outlook** automaticky přidá následující tři obslužné rutiny události do souboru kódu oblasti formuláře.

|Událost|Popis|
|-----------|-----------------|
|FormRegionInitializing|Vyvolá se před inicializací oblasti formuláře. Můžete kontrolovat podmínky v této obslužné rutině události a určit, zda má aplikace Outlook zobrazit oblast formuláře. Další informace najdete v tématu [jak: Zabrání aplikaci Outlook v zobrazení oblasti](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)formuláře.|
|FormRegionShowing|Vyvolá se po vytvoření instance oblasti formuláře, ale před zobrazením této oblasti.|
|FormRegionClosed|Vyvolá se před uzavřením oblasti formuláře.|

## <a name="Building"></a>Sestavení projektu
 Při sestavování projektu doplňku VSTO pro aplikaci Outlook, který obsahuje oblast formuláře, Visual Studio přidá do registru následující informace:

- Klíč pro každou třídu zprávy, která je přidružena k jedné nebo více oblastem formuláře.

- Záznam pro každou oblast formuláře a přidruženou hodnotu, která představuje název doplňku VSTO pro Outlook.

  Aplikace Outlook používá tyto informace k načtení oblastí formuláře.

## <a name="Debugging"></a>Ladění oblasti formuláře
 Doplněk VSTO pro Outlook, který obsahuje oblast formuláře, můžete ladit stejně, jako byste mohli ladit jiné [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty. Při spuštění [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicího programu Visual Studio automaticky spustí aplikaci Outlook.

 Chcete-li zobrazit oblast formuláře, je nutné otevřít příslušnou položku aplikace Outlook. Například pokud je přidaný region sousedícího formuláře připojen k dolní části položky pošty, otevřete položku Pošta.

## <a name="Deploying"></a>Nasazení oblasti formuláře
 Oblasti formulářů se nasazují automaticky s přidruženým doplňkem VSTO pro Outlook. Proto není nutné provádět žádné zvláštní úlohy pro nasazení oblasti formuláře. Další informace o nasazení doplňků VSTO najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Pokyny pro vytváření oblastí formulářů aplikace Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Poskytuje informace, které vám pomůžou optimalizovat oblasti formuláře a vyhnout se potenciálním problémům.|
|[Postupy: Přidání oblasti formuláře do projektu doplňku pro Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Ukazuje, jak vytvořit oblast formuláře pro rozšiřování standardního nebo vlastního systém Microsoft Officeho formuláře Outlooku pomocí Průvodce vytvořením **nové oblasti formuláře Outlooku** .|
|[Přidružení oblasti formuláře k třídě zpráv aplikace Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Vysvětluje, jak určit, které systém Microsoft Office položky Outlooku zobrazí oblast formuláře přidružením oblasti formuláře k třídě zpráv každé položky.|
|[Návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md)|Ukazuje, jak navrhnout vlastní oblast formuláře, která se zobrazí jako nová stránka v okně inspektoru položky kontaktu.|
|[Návod: Import oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Ukazuje, jak navrhnout oblast formuláře v aplikaci systém Microsoft Office Outlook a pak importovat oblast formuláře do projektu doplňku aplikace Outlook VSTO pomocí Průvodce vytvořením **nové oblasti formuláře Outlooku** .|
|[Přístup k oblasti formuláře v době běhu](../vsto/accessing-a-form-region-at-run-time.md)|Popisuje, jak napsat kód pro zobrazení, skrytí nebo úpravu ovládacích prvků v oblasti formuláře a umožnění uživatelům spustit kód z jiných oblastí v projektu pomocí `Globals` třídy.|
|[Postupy: Zabránit zobrazení oblasti formuláře v aplikaci Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Ukazuje, jak zabránit aplikaci systém Microsoft Office Outlook v zobrazení oblasti formuláře pro konkrétní položku.|
|Ukazuje, jak získat přístup k položce aplikace Outlook, ve které se zobrazuje oblast formuláře.|
|[Vlastní akce v oblastech formulářů aplikace Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Popisuje, jak uživatelům povolit reakci na položku Outlooku.|
