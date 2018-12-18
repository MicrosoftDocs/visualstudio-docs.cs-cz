---
title: Přidat nové zdroje dat
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fe32424632d06ed637b41dcd3d4b614afde369bd
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304607"
---
# <a name="add-new-data-sources"></a>Přidat nové zdroje dat

V kontextu dat nástroje .NET v sadě Visual Studio termín *zdroj dat* odkazují na objekty .NET, které se připojit k úložišti dat a zpřístupnit data pro aplikace .NET. Návrháři aplikace Visual Studio může spotřebovat výstup zdroje dat vygenerujte často používaný kód, který váže data formuláře, když přetahujete databázových objektů z **zdroje dat** okna. Tento druh zdroje dat může být:

- Třída v modelu Entity Framework, která souvisí s nějaký druh databáze.

- Datová sada, která souvisí s nějaký druh databáze.

- Třída, která představuje síťovou službu jako je například data služby Windows Communication Foundation (WCF) nebo službu REST.

- Třída zastupující služby SharePoint.

- Třída nebo kolekce ve vašem řešení.

> [!NOTE]
> Pokud nepoužíváte funkce vázání dat, datové sady, Entity Framework, LINQ to SQL, WCF nebo SharePoint, pojmu "zdroj dat" neplatí. Stačí se připojit přímo k databázi pomocí objektů třídy SQLCommand a komunikují přímo s databází.

Vytvoření a úprava zdroje dat pomocí **Průvodce konfigurací zdroje dat** v aplikaci Windows Forms nebo Windows Presentation Foundation. Rozhraní Entity Framework, nejprve vytvořit třídy entity a pak spusťte průvodce kliknutím na položku **projektu** > **přidat nový zdroj dat** (popsáno podrobněji dále v tomto článku).

![Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>okno Zdroje dat

Po vytvoření zdroje dat se zobrazí v **zdroje dat** panelu nástrojů.

> [!TIP]
> Chcete-li otevřít **zdroje dat** okno, ujistěte se, že váš projekt je otevřít a stiskněte klávesu **Shift**+**Alt**+**D**nebo zvolte **zobrazení** > **ostatní Windows** > **zdroje dat**.

Můžete přetáhnout zdroje dat z **zdroje dat** okno na návrhovou plochu formuláře nebo ovládacího prvku. To způsobí, že často používaný kód chcete vygenerovat, která zobrazí data z úložiště dat.

Následující obrázek ukazuje datovou sadu, která byla vyřazena, do formuláře Windows. Pokud vyberete **F5** na aplikaci, v ovládacích prvcích ve formuláři se zobrazí data z databáze.

![Operace přetažení zdroje dat](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Zdroj dat pro databáze nebo databázového souboru

Můžete vytvořit datové sady nebo model Entity Framework použít jako zdroj dat pro databáze nebo databázového souboru.

### <a name="dataset"></a>Datová sada

Pokud chcete vytvořit datovou sadu jako zdroj dat, spusťte **Průvodce konfigurací zdroje dat** tak, že vyberete **projektu** > **přidat nový zdroj dat**. Zvolte **databáze** zdroj dat typu a postupujte podle výzev a zadejte připojení nové nebo existující databáze nebo databázového souboru.

### <a name="entity-classes"></a>Tříd entit

Vytvoření modelu Entity Framework jako zdroj dat:

1. Spustit **Průvodce datovým modelem Entity** k vytvoření tříd entit. Vyberte **projektu** > **přidat novou položku** > **ADO.NET Entity Data Model**.

   ![Nové položky projektu model Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Zvolte metodu, která mají generovat model podle.

   ![Průvodce datovým modelem entity](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Přidáte jako zdroj dat modelu. Generované třídy joinkind **Průvodce konfigurací zdroje dat** při výběru **objekty** kategorie.

   ![Průvodce konfigurací zdroje dat pomocí tříd entit](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Zdroj dat pro službu

Chcete-li vytvořit zdroj dat ze služby, spusťte **Průvodce konfigurací zdroje dat** a zvolte **služby** zdroj dat typu. Toto je jenom zástupce **přidat odkaz na službu** dialogové okno, které se můžete dostat taky kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a vyberete **přidat odkaz na službu**.

Při vytváření zdroje dat ze služby Visual Studio přidá odkaz na službu do projektu. Visual Studio také vytvoří proxy objekty, které odpovídají objektům, které služba vrací. Například služba, která vrací třídu dataset v projektu reprezentována jako datová sada; Služba, která vrátí konkrétní typ je vyjádřen v projektu jako typ vrácena.

Vytvořit zdroj dat z následujících typů služeb:

- [Datové služby WCF](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Služby WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- webové služby

    > [!NOTE]
    > Položky, které se zobrazují v **zdroje dat** okna jsou závislé na datech, která služba vrací. Některé služby nemusí poskytnout dostatek informací, **Průvodce konfigurací zdroje dat** vytvořil objekty. Například pokud služba vrátí netypovou datovou sadu, žádné položky, které se zobrazí v **zdroje dat** okno po dokončení průvodce. Toto je vzhledem k tomu, že netypové datové sady neposkytují schéma, a proto Průvodce nemá dostatek informací pro vytvoření zdroje dat.

## <a name="data-source-for-an-object"></a>Zdroj dat pro objekt

Můžete vytvořit zdroj dat z libovolného objektu, který zpřístupňuje jeden nebo více veřejných vlastností spuštěním **Průvodce konfigurací zdroje dat** a následným výběrem **objekt** zdroj dat typu. Všechny veřejné vlastnosti objektu jsou zobrazeny v **zdroje dat** okna. Pokud používáte Entity Framework a vygenerování modelu, je to, kde najít tříd entit, které jsou zdroje dat pro vaši aplikaci.

Na **vyberte datové objekty** stránce, rozbalte uzly ve stromovém zobrazení objekty, které chcete svázat. Stromové zobrazení obsahuje uzly pro váš projekt a sestavení a jiné projekty, na které odkazuje váš projekt.

Pokud chcete vytvořit vazbu na objekt v sestavení nebo projektu, které nejsou uvedené ve stromovém zobrazení, klikněte na tlačítko **přidat odkaz** a použít **dialogové okno Přidání referenční** přidat odkaz na sestavení nebo projekt. Po přidání odkazu na sestavení nebo projekt se přidá do zobrazení stromu.

> [!NOTE]
> Budete muset sestavit projekt, který obsahuje objekty před objekty se zobrazí ve stromovém zobrazení.

> [!NOTE]
> Pro podporu a přetahování datové vazby, které implementují objekty <xref:System.ComponentModel.ITypedList> nebo <xref:System.ComponentModel.IListSource> rozhraní musí mít výchozí konstruktor. V opačném případě sady Visual Studio nelze vytvořit instanci objektu zdroje dat a zobrazí chyba, když přetáhnete položku na návrhovou plochu.

## <a name="data-source-for-a-sharepoint-list"></a>Zdroj dat pro seznam Sharepointu

Zdroj dat ze Sharepointového seznamu můžete vytvořit spuštěním **Průvodce konfigurací zdroje dat** a vyberete **SharePoint** typ zdroje dat. SharePoint poskytuje data prostřednictvím služeb WCF Data Services, takže vytvoření zdroje dat SharePoint je stejné jako vytvoření zdroje dat ze služby. Výběr **SharePoint** položky v **Průvodce konfigurací zdroje dat** otevře **přidat odkaz na službu** dialogové okno, kde se připojíte k datové službě SharePoint najetím myší na SharePoint server. To vyžaduje sadu SDK služby SharePoint.

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)