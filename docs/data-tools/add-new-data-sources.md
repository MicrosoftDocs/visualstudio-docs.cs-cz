---
title: Přidání nových zdrojů dat
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 555d32eb295e944060d2efe0b843e9d157b7c675
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302250"
---
# <a name="add-new-data-sources"></a>Přidání nových zdrojů dat

V kontextu datových nástrojů .NET v sadě Visual Studio termín *zdroj dat* odkazuje na objekty .NET, které se připojují k úložišti dat a zpřístupní data aplikaci .NET. Návrháři sady Visual Studio mohou spotřebovat výstup zdroje dat ke generování často používaného kódu, který sváže data s formuláři při přetahování databázových objektů z okna **Zdroje dat.** Tento druh zdroje dat může být:

- Třída v modelu entity framework, který je přidružen k nějakému druhu databáze.

- Datová sada, která je přidružena k nějakému druhu databáze.

- Třída, která představuje síťovou službu, jako je například datová služba WCF (Windows Communication Foundation) nebo služba REST.

- Třída, která představuje službu SharePoint.

- Třída nebo kolekce ve vašem řešení.

> [!NOTE]
> Pokud nepoužíváte funkce datové vazby, datové sady, entity framework, LINQ na SQL, WCF nebo SharePoint, koncept "zdroje dat" se nevztahuje. Stačí se připojit přímo k databázi pomocí objektů SQLCommand a komunikovat přímo s databází.

Zdroje dat můžete vytvářet a upravovat pomocí **Průvodce konfigurací zdroje dat** v aplikaci Windows Forms nebo Windows Presentation Foundation. V rámci entity nejprve vytvořte třídy entit a potom spusťte průvodce výběrem **možnosti Přidat** > **nový zdroj dat** projektu (podrobněji popsáno dále v tomto článku).

![Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>okno Zdroje dat

Po vytvoření zdroje dat se zobrazí v okně nástroje **Zdroje dat.**

> [!TIP]
> Chcete-li otevřít okno **Zdroje dat,** zkontrolujte, zda je projekt otevřený, a stiskněte **klávesu Shift**+**Alt**+**D** nebo zvolte **Zobrazit** > jiné**zdroje dat systému****Windows** > .

Zdroj dat můžete přetáhnout z okna **Zdroje dat** na návrhovou plochu nebo ovládací prvek formuláře. To způsobí, že často používaný kód, který má být generován, který zobrazuje data z úložiště dat.

Následující obrázek znázorňuje datovou sadu, která byla vynechána do formuláře systému Windows. Pokud v aplikaci vyberete **možnost F5,** data z podkladové databáze se zobrazí v ovládacích prvcích formuláře.

![Operace přetahování zdrojem dat](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Zdroj dat pro databázi nebo databázový soubor

Můžete vytvořit datovou sadu nebo model entity framework u použít jako zdroj dat pro databázi nebo databázový soubor.

### <a name="dataset"></a>Datová sada

Chcete-li vytvořit datovou sadu jako zdroj dat, spusťte **Průvodce konfigurací zdroje dat** výběrem **možnosti Přidat** > nový**zdroj dat**projektu . Zvolte typ zdroje dat **databáze** a podle pokynů určete nové nebo existující databázové připojení nebo databázový soubor.

### <a name="entity-classes"></a>Třídy entit

Vytvoření modelu entity frameworkjako zdroj dat:

1. Spusťte **Průvodce datovým modelem entity** a vytvořte třídy entit. Vyberte **možnost Přidat** > **novou položku** > **ADO.NET datového modelu entity**.

   ![Položka projektu modelu nového rámce entity](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Zvolte metodu, kterou chcete model generovat.

   ![Průvodce datovým modelem entity](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Přidejte model jako zdroj dat. Generované třídy se zobrazí v **Průvodci konfigurací zdroje dat,** když zvolíte kategorii **Objekty.**

   ![Průvodce konfigurací zdroje dat s třídami entit](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Zdroj dat pro službu

Chcete-li vytvořit zdroj dat ze služby, spusťte **Průvodce konfigurací zdroje dat** a zvolte typ zdroje dat **služby.** Toto je pouze zástupce dialogového okna **Přidat odkaz na službu,** ke kterému můžete získat přístup také klepnutím pravým tlačítkem myši na projekt v **Průzkumníku řešení** a výběrem **možnosti Přidat odkaz na službu**.

Při vytváření zdroje dat ze služby visual studio přidá odkaz na službu do projektu. Visual Studio také vytvoří proxy objekty, které odpovídají objekty, které služba vrátí. Například služba, která vrací datovou sadu, je v projektu reprezentována jako datová sada; služba, která vrací určitý typ je reprezentován v projektu jako typ vrátil.

Zdroj dat můžete vytvořit z následujících typů služeb:

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Služby WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Webové služby

    > [!NOTE]
    > Položky, které se zobrazí v okně **Zdroje dat,** jsou závislé na datech, která služba vrátí. Některé služby nemusí poskytnout dostatek informací pro **Průvodce konfigurací zdroje dat** k vytvoření objektů, které lze vázat. Pokud například služba vrátí nezadaný datový soubor, po dokončení průvodce se v okně **Zdroje dat** nezobrazí žádné položky. Důvodem je, že netypové datové sady neposkytují schéma, a proto průvodce nemá dostatek informací k vytvoření zdroje dat.

## <a name="data-source-for-an-object"></a>Zdroj dat pro objekt

Zdroj dat můžete vytvořit z libovolného objektu, který zpřístupňuje jednu nebo více veřejných vlastností spuštěním **Průvodce konfigurací zdroje dat** a výběrem typu zdroje dat **objektu.** Všechny veřejné vlastnosti objektu jsou zobrazeny v okně **Zdroje dat.** Pokud používáte entity Framework a vygenerovali model, je to místo, kde najdete entity třídy, které jsou zdroje dat pro vaši aplikaci.

Na stránce **Vybrat datové objekty** rozbalte uzly ve stromovém zobrazení a vyhledejte objekty, se kterými chcete vytvořit vazbu. Stromové zobrazení obsahuje uzly pro projekt a pro sestavení a další projekty, na které projekt odkazuje.

Pokud chcete vytvořit vazbu na objekt v sestavě nebo projektu, který se nezobrazuje ve stromovém zobrazení, klepněte na **tlačítko Přidat odkaz** a pomocí **dialogového okna Přidat odkaz** přidejte odkaz na sestavení nebo projekt. Po přidání odkazu je sestavení nebo projekt přidán do stromového zobrazení.

> [!NOTE]
> Možná budete muset vytvořit projekt, který obsahuje objekty před objekty se zobrazí ve stromovém zobrazení.

> [!NOTE]
> Chcete-li podporovat datové vazby přetažení, <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> objekty, které implementují rozhraní nebo musí mít výchozí konstruktor. V opačném případě visual studio nemůže vytvořit konkretizovat objekt zdroje dat a zobrazí chybu při přetažení položky na návrhovou plochu.

## <a name="data-source-for-a-sharepoint-list"></a>Zdroj dat pro sharepointový seznam

Zdroj dat můžete vytvořit ze seznamu služby SharePoint spuštěním **Průvodce konfigurací zdroje dat** a výběrem typu zdroje dat **služby SharePoint.** SharePoint zveřejňuje data prostřednictvím služby WCF Data Services, takže vytvoření zdroje dat služby SharePoint je stejné jako vytvoření zdroje dat ze služby. Když vyberete **položku SharePointu** v **Průvodci konfigurací zdroje dat,** otevře se dialogové okno **Přidat odkaz na službu,** ve kterém se připojíte k datové službě SharePoint, a to tak, že přejdete na sharepointový server. To vyžaduje sharepointovou sadu SDK.

## <a name="see-also"></a>Viz také

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
