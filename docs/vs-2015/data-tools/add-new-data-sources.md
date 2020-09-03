---
title: Přidat nové zdroje dat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85c07ad7995bc614df4b988bb17fa8977452b5d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673066"
---
# <a name="add-new-data-sources"></a>Přidání nových zdrojů dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V kontextu nástrojů .NET Data Tools v sadě Visual Studio pojem *zdroj dat* odkazuje na objekty .NET, které se připojují k úložišti dat a zpřístupňují data aplikaci .NET. Návrháři sady Visual Studio mohou využívat výstup zdroje dat, aby vygenerovaly často používaný kód, který váže data na formuláře při přetahování objektů databáze z okna **zdroje dat** . Tento druh zdroje dat může být:

- Třída v modelu Entity Framework, která je přidružena k určitému druhu databáze.

- Datová sada, která je přidružena k určitému typu databáze.

- Třída, která představuje síťovou službu, například datovou službu Windows Communication Foundation (WCF) nebo službu REST.

- Třída, která představuje službu SharePoint.

- Třída nebo kolekce ve vašem řešení.

> [!NOTE]
> Pokud nepoužíváte funkce datových vazeb, datové sady, Entity Framework, LINQ to SQL, WCF nebo SharePoint, koncept zdroje dat se nevztahuje. Stačí se připojit přímo k databázi pomocí objektů SQLCommand a přímo komunikovat s databází.

 Zdroje dat můžete vytvářet a upravovat pomocí **Průvodce konfigurací zdroje dat** v aplikaci model Windows Forms nebo Windows Presentation Foundation. Pro Entity Framework nejprve vytvořte třídy entit a potom spusťte Průvodce výběrem možnosti **projekt**  >  **Přidat nový zdroj dat** (podrobněji popsané dále v tomto článku).

 ![Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png "Průvodce konfigurací zdroje dat")

 Po vytvoření zdroje dat se zobrazí v okně nástroje **zdroje dat** (SHIFT + ALT + D nebo **Zobrazit**  >  **jiný**  >  **zdroj dat**Windows). Zdroj dat můžete přetáhnout z okna **zdroje dat** na návrhovou plochu formuláře nebo ovládací prvek. To způsobí vygenerování často používaného kódu – kód, který zobrazí data, která pocházejí z úložiště dat pro uživatele. Následující ilustrace znázorňuje datovou sadu, která byla vyřazena do formuláře Windows Form. Pokud jste v aplikaci vybrali F5, data z podkladové databáze se zobrazí v ovládacích prvcích formuláře.

 ![Operace přetažení zdroje dat](../data-tools/media/raddata-data-source-drag-operation.png "operace přetažení zdroje dat raddata")

## <a name="data-source-for-a-database-or-a-database-file"></a>Zdroj dat pro databázi nebo databázový soubor

### <a name="dataset"></a>Datová sada
 Chcete-li vytvořit datovou sadu jako zdroj dat, spusťte **Průvodce konfigurací zdroje dat** (**projekt**  >  **přidejte nový zdroj dat** ) a vyberte typ zdroje dat **databáze** . Podle pokynů zadejte nové nebo existující připojení k databázi nebo databázový soubor.

### <a name="entity-classes"></a>Třídy entit
 Chcete-li vytvořit model Entity Framework jako zdroj dat, nejprve spusťte **Průvodce model EDM (Entity Data Model)** a vytvořte třídy entit (**projekt**  >  **přidejte novou položku**  >  **ADO.NET model EDM (Entity Data Model)**).

 ![Nová položka projektu Entity Framework modelu](../data-tools/media/raddata-new-entity-framework-model-project-item.png "Položka projektu raddata nové Entity Framework modelu")

 Vyberte metodu, podle které chcete model vygenerovat.

 ![Průvodce model EDM (Entity Data Model)](../data-tools/media/raddata-entity-data-model-wizard.png "Průvodce model EDM (Entity Data Model) raddata")

 Přidejte model jako zdroj dat. Třídy, které byly generovány, se zobrazí v **Průvodci konfigurací zdroje dat** při výběru kategorie **objekty** .

 ![Průvodce konfigurací zdroje dat s třídami entit](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "Průvodce konfigurací zdroje dat raddata s třídami entit")

## <a name="data-source-for-a-service"></a>Zdroj dat pro službu
 Chcete-li vytvořit zdroj dat ze služby, spusťte **Průvodce konfigurací zdroje dat** a vyberte typ zdroje dat **služby** . To je opravdu pouze zástupce dialogového okna **Přidat odkaz na službu** , ke kterému lze také získat přístup kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení** a výběrem možnosti **Přidat odkaz na službu**.

 Když vytvoříte zdroj dat ze služby, Visual Studio přidá do projektu odkaz na službu. Visual Studio také vytvoří proxy objekty, které odpovídají objektům, které vrací služba. Například služba, která vrací datovou sadu, je v projektu reprezentována jako datová sada; služba, která vrací konkrétní typ, je v projektu reprezentována jako vrácený typ.

 Zdroj dat můžete vytvořit z následujících typů služeb:

- WCF Data Services. Další informace najdete v tématu [Přehled](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- WCF Data Services. Další informace naleznete v tématu [Windows Communication Foundation Services a WCF Data Services v aplikaci Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).

- Webové služby.

    > [!NOTE]
    > Položky, které se zobrazí v okně **zdroje dat** , jsou závislé na datech, která služba vrací. Některé služby nemusí poskytnout dostatek informací pro **Průvodce konfigurací zdroje dat** pro vytváření objektů s možností vazby. Například pokud služba vrátí netypové datové sady, po dokončení průvodce se nezobrazí žádné položky v okně **zdroje dat** . Důvodem je, že netypové datové sady neposkytují schéma, a proto průvodce nemá k dispozici dostatek informací pro vytvoření zdroje dat.

## <a name="data-source-for-an-object"></a>Zdroj dat pro objekt
 Můžete vytvořit zdroj dat z libovolného objektu, který zveřejňuje jednu nebo více veřejných vlastností spuštěním **Průvodce konfigurací zdroje dat** a výběrem typu zdroje dat **objektu** . Všechny veřejné vlastnosti objektu se zobrazí v okně **zdroje dat** .   Používáte-li Entity Framework a vygenerovali jste model, toto je místo, kde najdete třídy entit, které budou zdrojem dat pro vaši aplikaci.

 Na stránce **Vybrat datové objekty** rozbalte uzly ve stromovém zobrazení a vyhledejte objekty, se kterými chcete vytvořit vazby. Stromové zobrazení obsahuje uzly pro váš projekt a pro sestavení a další projekty, na které je odkazováno v projektu.

 Chcete-li vytvořit propojení s objektem v sestavení nebo projektu, které se nezobrazují ve stromovém zobrazení, klikněte na tlačítko **Přidat odkaz** a pomocí **dialogového okna Přidat odkaz** přidejte odkaz na sestavení nebo projekt. Po přidání odkazu je sestavení nebo projekt přidáno do stromového zobrazení.

> [!NOTE]
> Možná budete muset sestavit projekt, který obsahuje vaše objekty před tím, než se objekty zobrazí ve stromovém zobrazení.

> [!NOTE]
> Aby bylo možné podporovat přetahování datových vazeb, objekty, které implementují <xref:System.ComponentModel.ITypedList> rozhraní nebo, <xref:System.ComponentModel.IListSource> musí mít výchozí konstruktor. V opačném případě Visual Studio nemůže vytvořit instanci objektu zdroje dat a při přetahování položky na návrhovou plochu se zobrazí chyba.

## <a name="data-source-for-a-sharepoint-list"></a>Zdroj dat pro SharePointový seznam
 Zdroj dat můžete vytvořit ze SharePointového seznamu spuštěním **Průvodce konfigurací zdroje dat** a výběrem typu zdroje dat **služby SharePoint** . SharePoint zpřístupňuje data prostřednictvím [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] , takže vytvoření zdroje dat SharePointu je stejné jako vytvoření zdroje dat ze služby. Výběr položky **služby SharePoint** v **Průvodci konfigurací zdroje dat** otevře dialogové okno **Přidat odkaz na službu** , kde se připojíte ke službě SharePoint data Service tak, že přejdete na server SharePoint.  To vyžaduje sadu SharePoint SDK.

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
