---
title: Vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje rozšířené datové vazby | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de22f93c6fd04f89360fdaf8a2f5d83bd373d93d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284255"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje komplexní datovou vazbu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Při zobrazení dat ve formulářích v aplikacích Windows, můžete vybrat z existujících ovládacích prvků **nástrojů**, nebo můžete vytvořit vlastní ovládací prvky, pokud vaše aplikace vyžaduje funkce, které nejsou k dispozici ve standardní ovládací prvky. Tento návod ukazuje, jak vytvořit ovládací prvek, který implementuje <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Ovládací prvky, které implementují <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> obsahovat `DataSource` a `DataMember` vlastnost, která může být vázaný na data. Tyto ovládací prvky jsou podobné <xref:System.Windows.Forms.DataGridView> nebo <xref:System.Windows.Forms.ListBox>.  
  
 Další informace o vytváření ovládacího prvku, naleznete v tématu [vývoj prvky Windows Forms v době návrhu](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Při vytváření ovládacích prvků pro použití ve scénářích datové vazby, budete muset implementovat jedno z následujících atributů datové vazby:  
  
|Použití atributu vázání dat|  
|-----------------------------------|  
|Implementace <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na jednoduché ovládací prvky, jako je <xref:System.Windows.Forms.TextBox>, který zobrazí jeden sloupec (nebo vlastnost) dat. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementace <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.DataGridView>, který zobrazí seznamy (nebo tabulky) data. (Tento proces je popsán v této stránce průvodce.)|  
|Implementace <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na ovládací prvky, jako je <xref:System.Windows.Forms.ComboBox>, který zobrazí seznamy (nebo tabulky) data, ale také budete muset k dispozici do jednoho sloupce nebo vlastnosti. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Tento návod vytvoří komplexní ovládací prvek, který zobrazuje řádky dat z tabulky. V tomto příkladu `Customers` tabulky z ukázkové databáze Northwind. Komplexní uživatelský ovládací prvek zobrazí tabulku customers v <xref:System.Windows.Forms.DataGridView> v vlastního ovládacího prvku.  
  
 V tomto návodu se dozvíte, jak:  
  
-   Vytvořte nový **aplikace Windows**.  
  
-   Přidat nový **uživatelský ovládací prvek** do projektu.  
  
-   Vizuální návrh uživatelského ovládacího prvku.  
  
-   Implementace `ComplexBindingProperty` atribut.  
  
-   Vytvoření datové sady [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Nastavte **zákazníkům** tabulku v [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) používat nový komplexní ovládací prvek.  
  
-   Přidat nový ovládací prvek z jeho přetažením **okna zdroje dat** do **Form1**.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Přístup k ukázkové databázi Northwind. Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Vytvoření aplikace Windows  
 Prvním krokem je vytvoření **aplikace Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows  
  
1.  V sadě Visual Studio z **souboru** nabídky, vytvořte nový **projektu**.  
  
2.  Pojmenujte projekt **ComplexControlWalkthrough**.  
  
3.  Vyberte **aplikace Windows**a klikněte na tlačítko **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **ComplexControlWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu  
 Protože tento návod vytvoří komplexní data neumožňující vazbu ovládacího prvku z **uživatelský ovládací prvek**, je nutné přidat **uživatelský ovládací prvek** položky do projektu.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Chcete-li přidat uživatelský ovládací prvek do projektu  
  
1.  Z **projektu** nabídce zvolte **přidat uživatelský ovládací prvek**.  
  
2.  Typ **ComplexDataGridView** v **název** oblasti a pak klikněte na tlačítko **přidat**.  
  
     **ComplexDataGridView** ovládací prvek je přidán do **Průzkumníka řešení**a otevře v návrháři.  
  
## <a name="design-the-complexdatagridview-control"></a>Návrh ComplexDataGridView ovládacího prvku  
 Tento krok přidává <xref:System.Windows.Forms.DataGridView> uživatelského ovládacího prvku.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>Chcete-li navrhnout ComplexDataGridView ovládacího prvku  
  
-   Přetáhněte <xref:System.Windows.Forms.DataGridView> z **nástrojů** na návrhové ploše uživatelský ovládací prvek.  
  
## <a name="add-the-required-data-binding-attribute"></a>Přidat požadovaný atribut vázání dat  
 Pro komplexní ovládací prvky, že vazba dat podpory, můžete implementovat <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>K implementaci atribut ComplexBindingProperties  
  
1.  Přepnout **ComplexDataGridView** ovládacího prvku na zobrazení kódu. (Na **zobrazení** nabídce vyberte možnost **kód**.)  
  
2.  Nahraďte kód v `ComplexDataGridView` následujícím kódem:  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  Z **sestavení** nabídce zvolte **sestavit řešení**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze  
 Tento krok používá **konfigurace zdroje dat** průvodce k vytvoření zdroje dat na základě `Customers` tabulky v ukázkové databázi Northwind. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o instalaci ukázkové databáze Northwind naleznete v tématu [instalace SQL serveru, ukázkové databáze](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **konfigurace zdroje dat** průvodce.  
  
3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.  
  
4.  Na **vyberte datové připojení** stránka provádění, jednu z následujících akcí:  
  
    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.  
  
    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.  
  
5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.  
  
6.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.  
  
7.  Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** uzlu.  
  
8.  Vyberte `Customers` tabulku a pak klikněte na tlačítko **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a `Customers` se zobrazí v tabulce **zdroje dat** okna.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Nastavit pomocí ovládacího prvku ComplexDataGridView tabulky Zákazníci  
 V rámci **zdroje dat** okně můžete nastavit ovládacího prvku má být vytvořen před přetažení položek do formuláře.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Chcete-li nastavit tabulce Zákazníci k vytvoření vazby na ovládací prvek ComplexDataGridView  
  
1.  Otevřít **Form1** v návrháři.  
  
2.  Rozbalte **zákazníkům** uzlu **zdroje dat** okno.  
  
3.  Klikněte na šipku rozevíracího seznamu **zákazníkům** uzel a zvolte **vlastní**.  
  
4.  Vyberte **ComplexDataGridView** ze seznamu **přidružené ovládací prvky** v **možnosti přizpůsobení uživatelského rozhraní dat** dialogové okno.  
  
5.  Klikněte na šipku rozevíracího seznamu `Customers` tabulce a zvolte **ComplexDataGridView** ze seznamu ovládacích prvků.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols do formuláře  
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři  
  
-   Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do formuláře. Ověřte, že **ComplexDataGridView** ovládacího prvku se používá k zobrazení dat v tabulce.  
  
## <a name="running-the-application"></a>Spuštění aplikace  
  
#### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
-   Stisknutím klávesy F5 spusťte aplikaci.  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete provést po vytvoření ovládacího prvku, který podporuje datové vazby. Některé typické další postup je následující:  
  
-   Umístění vlastních ovládacích prvků do knihovny ovládacích prvků, lze je použít v jiných aplikacích.  
  
-   Vytváření ovládacích prvků, které podporují scénáře vyhledávání. Další informace najdete v tématu [vytvoření uživatelského ovládacího prvku Windows Forms, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows Forms – ovládací prvky](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)

