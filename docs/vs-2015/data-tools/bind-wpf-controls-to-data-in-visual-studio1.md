---
title: Vázání ovládacích prvků WPF k datům | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 12aad1f22fdc4badc024c62fbc302eef8e3937e4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670078"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data můžete uživatelům vaší aplikace zobrazit tak, že data svážete s ovládacími prvky [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)]. Chcete-li vytvořit tyto ovládací prvky vázané na data, můžete přetáhnout položky z okna **zdroje dat** do [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Toto téma popisuje některé nejběžnější úlohy, nástroje a třídy, které lze použít k vytváření aplikací [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] vázaných na data.

 Obecné informace o tom, jak vytvořit ovládací prvky vázané na data v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], naleznete v tématu [BIND Controls to data in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Další informace o [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] datové vazby najdete v tématu [Přehled datových vazeb](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Úlohy, které jsou součástí vazby ovládacích prvků WPF na data
 V následující tabulce jsou uvedeny úlohy, které lze provést přetažením položek z okna **zdroje dat** do [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)].

|Úloha|Další informace|
|----------|----------------------|
|Vytvořte nové ovládací prvky vázané na data.<br /><br /> Navažte existující ovládací prvky na data.|[Vázání ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [BIND ovládacího prvku WPF na datovou sadu](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Vytvořte ovládací prvky zobrazující související data ve vztahu nadřazený-podřízený, když uživatel vybere nadřazený záznam dat v jednom ovládacím prvku, jiný ovládací prvek pro tento vybraný záznam zobrazí související podřízená data.|[Zobrazení souvisejících dat v aplikacích WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Vytvoří *vyhledávací tabulku* , která zobrazí informace z jedné tabulky na základě hodnoty pole cizího klíče v jiné tabulce.|[Vytváření vyhledávacích tabulek v aplikacích WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Navažte ovládací prvek na obrázek v databázi.|[Vytvoření vazby ovládacích prvků k obrázkům z databáze](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Platné cíle přetažení
 Položky v okně **zdroje dat** lze přetahovat pouze do platných cílů přetažení v [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]. Existují dva hlavní druhy platných cílů přetažení: kontejnery a ovládací prvky. Kontejner je prvek uživatelského rozhraní, který obvykle obsahuje ovládací prvky. Kontejnerem je například mřížka nebo okno.

## <a name="generated-xaml-and-code"></a>Generovaný kód XAML a kód
 Když přetáhnete položku z okna **zdroje dat** do [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)], [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vygeneruje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] definující nový ovládací prvek vázaný na data (nebo vytvoří vazbu existujícího ovládacího prvku ke zdroji dat). U některých zdrojů dat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také generuje kód v souboru kódu na pozadí, který vyplní zdroj dat daty.

 V následující tabulce je uveden seznam [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a kód, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje pro každý typ zdroje dat v okně **zdroje dat** .

|Zdroj dat|Generování souboru XAML, který váže ovládací prvek na zdroj dat|Generování kódu, který vyplní daty zdroj dat|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Datová sada|Ano|Ano|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Ano|Ano|
|Služba|Ano|Ne|
|Objekt|Ano|Ne|

### <a name="datasets"></a>Datové sady
 Když přetáhnete tabulku nebo sloupec z okna **zdroje dat** do návrháře, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)], který provede následující akce:

- Přidá datovou sadu a novou <xref:System.Windows.Data.CollectionViewSource> do prostředků kontejneru, do kterého jste přetáhli položku. @No__t_0 je objekt, který lze použít k procházení a zobrazení dat v datové sadě.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři, XAML naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru, XAML vytvoří ovládací prvek, který byl vybrán pro přetaženou položku, a naváže ovládací prvek na položku. Ovládací prvek je vytvořen v novém <xref:System.Windows.Controls.Grid>.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také provede následující změny v souboru s kódem na pozadí:

- Vytvoří obslužnou rutinu události <xref:System.Windows.FrameworkElement.Loaded> pro prvek [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)], který obsahuje ovládací prvek. Obslužná rutina události vyplní tabulku daty, načte <xref:System.Windows.Data.CollectionViewSource> z prostředků kontejneru a následně provede první položku dat aktuální položkou. Pokud již obslužná rutina události <xref:System.Windows.FrameworkElement.Loaded> existuje, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přidá tento kód do existující obslužné rutiny události.

### <a name="entity-data-models"></a>Modely entity data model
 Když přetáhnete entitu nebo vlastnost entity z okna **zdroje dat** do návrháře, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)], který provede následující akce:

- Přidá novou <xref:System.Windows.Data.CollectionViewSource> do prostředků kontejneru, do kterého jste přetáhli položku. @No__t_0 je objekt, který lze použít k procházení a zobrazení dat v entitě.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] sváže ovládací prvek s položkou. Pokud přetáhnete položku do kontejneru, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] vytvoří ovládací prvek, který byl vybrán pro přetaženou položku, a naváže ovládací prvek na položku. Ovládací prvek je vytvořen v novém <xref:System.Windows.Controls.Grid>.

  Sada Visual Studio rovněž provede následující změny v souboru s kódem na pozadí:

- Přidá novou metodu, jež vrací dotaz pro entitu, kterou jste přetáhli do návrháře (nebo entitu obsahující vlastnost, kterou jste přetáhli do návrháře). Nová metoda má název Get*EntityName*Query, kde *EntityName* je název entity.

- Vytvoří obslužnou rutinu události <xref:System.Windows.FrameworkElement.Loaded> pro prvek [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)], který obsahuje ovládací prvek. Obslužná rutina události volá metodu Get*EntityName*Query pro vyplnění entit daty, načítá <xref:System.Windows.Data.CollectionViewSource> z prostředků kontejneru a následně provede první položku dat aktuální položkou. Pokud již obslužná rutina události <xref:System.Windows.FrameworkElement.Loaded> existuje, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přidá tento kód do existující obslužné rutiny události.

### <a name="services"></a>Služby
 Když přetáhnete objekt nebo vlastnost služby z okna **zdroje dat** do návrháře, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)], která vytvoří ovládací prvek vázaný na data (nebo naváže existující ovládací prvek na objekt nebo vlastnost). @No__t_0 však negeneruje kód, který vyplní objekt proxy služby daty. Tento kód musíte napsat sami. Příklad, který ukazuje, jak to provést, naleznete v tématu [BIND WPF Controls to a WCF Data Service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Sada Visual Studio generuje jazyk XAML, který provede následující akce:

- Přidá novou <xref:System.Windows.Data.CollectionViewSource> do prostředků kontejneru, do kterého jste přetáhli položku. @No__t_0 je objekt, který lze použít k procházení a zobrazení dat v objektu, který je vrácen službou.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] sváže ovládací prvek s položkou. Pokud přetáhnete položku do kontejneru, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] vytvoří ovládací prvek, který byl vybrán pro přetaženou položku, a naváže ovládací prvek na položku. Ovládací prvek je vytvořen v novém <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Objekty
 Při přetažení objektu nebo vlastnosti z okna **zdroje dat** do návrháře [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)], která vytvoří ovládací prvek vázaný na data (nebo naváže existující ovládací prvek na objekt nebo vlastnost). @No__t_0 však negeneruje kód pro vyplnění objektu daty. Tento kód musíte napsat sami.

> [!NOTE]
> Vlastní třídy musí být veřejné a ve výchozím nastavení mají konstruktor bez parametrů. Nemůžou být vnořené třídy, které mají ve své syntaxi tečku. Další informace naleznete v tématu [XAML a vlastní třídy pro WPF](https://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)], které provádí následující akce:

- Přidá novou <xref:System.Windows.Data.CollectionViewSource> do prostředků kontejneru, do kterého jste přetáhli položku. @No__t_0 je objekt, který lze použít k procházení a zobrazení dat v objektu.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři, XAML naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru, XAML vytvoří ovládací prvek, který byl vybrán pro přetaženou položku, a naváže ovládací prvek na položku. Ovládací prvek je vytvořen v novém <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
