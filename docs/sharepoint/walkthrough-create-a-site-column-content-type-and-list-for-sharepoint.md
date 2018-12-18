---
title: 'Návod: Vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2fb78f5c40a04bb69d2f95d7f872b05e3d501113
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900121"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Návod: Vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint
  Následující postupy ukazují, jak vytvořit vlastní sloupce webu služby SharePoint, nebo *pole*– stejně jako typ obsahu, který používá sloupce webu. Také ukazuje, jak vytvořit seznam, který používá nového typu obsahu.  
  
 Tento návod zahrnuje následující úlohy:  
  
- [Vytváření sloupců webu vlastní](#BKMK_CreatingCustSiteCols).  
  
- [Vytváří se vlastní typ obsahu](#BKMK_CreateCustContType).  
  
- [Vytvoření seznamu](#BKMK_CreateList).  
  
- [Vytvoření seznamu](#BKMK_CreateList).  
  
- [Testování aplikace](#BKMK_TestApp).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Podporované edice systému Windows a SharePoint.
  
-   Visual Studio.  
  
## <a name="create-custom-site-columns"></a>Vytvoření vlastní stránky sloupců
 Tento příklad vytvoří seznam pro správu pacientů v nemocnici. Nejprve musíte vytvořit projekt služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a přidat sloupce webu, následujícím způsobem.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Na [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **souboru** nabídce zvolte **nový** > **projektu**.  
  
2.  V **nový projekt** dialogové okno, v části **Visual C#** nebo **jazyka Visual Basic**, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010**.  
  
3.  V **šablony** podokně zvolte **projektu služby SharePoint 2010**, změňte název projekt tak, aby **Clinic**a klikněte na tlačítko **OK** tlačítko.  
  
     Šablona projektu služby SharePoint 2010 je prázdný projekt, který se používá v tomto příkladu tak, aby obsahovala sloupců webu a dalších položek projektu, které jsou přidány později.  
  
4.  Na **zadejte web a úroveň zabezpečení pro ladění** stránky, zadejte adresu URL pro místní Sharepointový web, ke kterému chcete přidat novou položku vlastní pole nebo použijte výchozí umístění (`http://<`*SystemName* `>/)`.  
  
5.  V **co je úroveň důvěryhodnosti pro toto řešení SharePoint?** oddílu, použijte výchozí hodnotu **nasadit jako řešení v izolovaném prostoru**.  
  
     Další informace o v izolovaném prostoru a farmách, přečtěte si [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Zvolte **Dokončit** tlačítko. Projekt by měl být nyní obsažena v **Průzkumníka řešení**.  
  
#### <a name="to-add-site-columns"></a>Chcete-li přidat sloupce webu  
  
1.  Přidáte nový sloupec webu. Chcete-li to provést, v **Průzkumníka řešení**, otevřete místní nabídku pro **Clinic**a klikněte na tlačítko **přidat** > **nová položka**.  
  
2.  V **přidat novou položku** dialogového okna zvolte **sloupce webu**, změňte název na **pacienta název**a klikněte na tlačítko **přidat** tlačítko.  
  
3.  Ve sloupci lokality *Elements.xml* souboru, ponechte **typ** nastavení jako **Text**a změnit **skupiny** nastavení  **Sloupce webu Clinic**. Po dokončení sloupce webu *Elements.xml* soubor by měl vypadat jako v následujícím příkladu.  
  
    ```xml  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  Další dva sloupce webu pomocí stejného postupu, přidejte do projektu: **pacienta ID** (typ = "Celočíselné") a **lékař název** (typ = "Text"). Nastavte na hodnotu jejich skupiny **sloupců webu Clinic**.  
  
## <a name="create-a-custom-content-type"></a>Vytvořit vlastní typ obsahu
 Dále vytvořte typu obsahu – na základě typu obsahu kontakty –, který obsahuje sloupce webu, které jste vytvořili v předchozím postupu. Podle typu obsahu založenou na stávající typ obsahu, můžete ušetřit čas, protože základní typ obsahu poskytuje několik sloupců webu pro použití v nového typu obsahu.  
  
#### <a name="to-create-a-custom-content-type"></a>Chcete-li vytvořit vlastní typ obsahu  
  
1.  Přidáte typ obsahu do projektu. Chcete-li to provést, v **Průzkumníka řešení**, zvolte uzel projektu  
  
2.  V panelu nabídky zvolte **projektu** > **přidat novou položku**.  
  
3.  V části **Visual C#** nebo **jazyka Visual Basic**, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
4.  V **šablony** podokně, vyberte **typ obsahu** šablony, změňte název na **informací o pacientech**a klikněte na tlačítko **přidat** tlačítko.  
  
     **Průvodce přizpůsobením SharePoint** otevře.  
  
5.  V **které základní typ obsahu by měl tento typ obsahu dědit z** klikněte na položku **kontakt** jako typ obsahu, na kterém chcete založit nový typ obsahu a klikněte na tlačítko **Dokončit**tlačítko.  
  
     To poskytuje přístup k ostatním sloupcům potenciálně užitečné webu v kontaktu typ obsahu, kromě sloupců webu, které jste definovali dříve.  
  
6.  Po typ obsahu návrháře zobrazení v **sloupce** kartu, přidejte tři sloupce, které jste definovali dříve webu: **pacienta název**, **pacienta ID**a **Lékař název**. Pro přidání těchto sloupců, vyberte v seznamu sloupců webu první seznam **zobrazovaný název**a pak zvolte každý sloupec v seznamu, jeden po druhém.  
  
    > [!TIP]  
    >  Seznam sloupců webu zvolte rychleji, můžete filtrovat tak, že zadáte několik prvních písmen názvu sloupce.  
  
7.  Kromě tři sloupce vlastního webu, přidejte **komentáře** sloupce webu ze seznamu sloupců webu.  
  
8.  Vyberte **požadované** zaškrtávací políčko pro **pacienta název** a **pacienta ID** sloupců webu, aby se daly požadovaných polí.  
  
9. Na **Content Type** kartu, ujistěte se, že je název typu obsahu **informací o pacientech**a potom změňte popis, který **kartu s informacemi o pacientech**.  
  
10. Změna **název skupiny** k **typy obsahu Clinic**a další nastavení ponechte na výchozích hodnotách.  
  
11. V panelu nabídky zvolte **souboru** > **Uložit vše**a pak zavřete návrháře typu obsahu.  
  
## <a name="create-a-list"></a>Vytvoření seznamu
 Teď vytvořte seznam, který používá novou obsahu sloupce typu a lokality.  
  
#### <a name="to-create-a-list"></a>Chcete-li vytvořit seznam  
  
1.  Přidání seznamu do projektu. Chcete-li to provést, v **Průzkumníka řešení**, zvolte uzel projektu.  
  
2.  V panelu nabídky zvolte **projektu** > **přidat novou položku**.  
  
3.  V části **Visual C#** nebo **jazyka Visual Basic**, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
4.  V **šablony** podokně, vyberte **seznamu** šablony, změňte název na **pacientů**a klikněte na tlačítko **přidat** tlačítko.  
  
5.  Nechte **vlastní seznam na základě** nastavení jako **výchozí (prázdné)** a klikněte na tlačítko **Dokončit** tlačítko.  
  
6.  V Návrháři seznamu zvolte **typy obsahu** tlačítka pro zobrazení **nastavení typu obsahu** dialogové okno.  
  
7.  Vyberte nový řádek, vyberte **informací o pacientech** obsah typu v seznamu typů obsahu a klikněte na tlačítko **OK** tlačítko.  
  
     To přidá všechny sloupce webu z **informací o pacientech** typ do seznamu obsahu.  
  
8.  Odstraňte všechny sloupce webu v seznamu s těmito výjimkami:  
  
    -   ID pacientů  
  
    -   Jméno pacienta  
  
    -   Telefon domů  
  
    -   E-mailu  
  
    -   Název lékař  
  
    -   Komentáře  
  
9. V části **zobrazovaný název sloupce**, zvolte na prázdný řádek, přidejte vlastní seznam sloupců a pojmenujte ho **nemocnice**. Ponechat jeho datový typ jako **jeden řádek textu**.  
  
     Vlastní seznam sloupců se vztahuje pouze na tento seznam. Při přidání vlastního seznamu sloupců do seznamu se nový seznam typ obsahu, včetně všech sloupců, přidá se do seznamu a nastavit jako výchozí seznam.  
  
    > [!TIP]  
    >  Pokud zvolíte sloupce ze seznamu sloupců webu, použije se existující sloupec webu. Nicméně pokud zadáte hodnotu pro název sloupce bez výběru žádné sloupce v seznamu, vlastní seznam sloupců je vytvořena, i v případě, že sloupce se stejným názvem již existuje v seznamu.  
  
     Volitelně můžete místo nastavení datový typ pro sloupec vlastní seznam, který se **jeden řádek textu**, může místo toho nastavte datový typ pro tento sloupec k vyhledávání a jeho hodnoty by načteny z tabulky nebo jiného seznamu. Informace o sloupcích vyhledávání najdete v tématu [vztahy seznamu v Sharepointu 2010](http://go.microsoft.com/fwlink/?LinkId=224994) a [vyhledávání a seznam relací](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Vedle položky **pacienta ID** a **pacienta název** polí, vyberte **vyžaduje** zaškrtávací políčko.  
  
11. Na **zobrazení** , vyberte prázdný řádek můžete vytvořit zobrazení. Zadejte **podrobnosti o pacientech**.  
  
     Na **zobrazení** kartu, můžete určit sloupce, které chcete zobrazit v seznamu služby SharePoint.  
  
12. Zvolte nový **podrobnosti o pacientech** řádek a klikněte na tlačítko **nastavit jako výchozí** tlačítko.  
  
     Výchozí zobrazení seznamu je nyní nové zobrazení.  
  
13. Přidejte následující sloupce, které chcete **vybrané sloupce** seznamu v následujícím pořadí:  
  
    -   ID pacientů  
  
    -   Jméno pacienta  
  
    -   Telefon domů  
  
    -   E-mailu  
  
    -   Název lékař  
  
    -   Nemocnice  
  
    -   Komentáře  
  
14. V **vlastnosti** klikněte na položku **řazení a seskupování** vlastnost a klikněte na tlačítko se třemi tečkami ![ikonu se třemi tečkami](../sharepoint/media/ellipsisicon.gif "ikonu se třemi tečkami")zobrazíte **řazení a seskupování** dialogové okno.  
  
15. V **název sloupce** klikněte na položku **pacienta název**, ujistěte se, že **řazení** sloupec je nastaven na **vzestupně**a klikněte na tlačítko  **OK** tlačítko.  
  
## <a name="test-the-application"></a>Testování aplikace
 Teď, když sloupců vlastního webu, typu obsahu a seznamu jsou připravené, nasadíte do služby SharePoint a spusťte aplikaci a otestovat ho.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  V panelu nabídky zvolte **souboru** > **Uložit vše**.  
  
2.  Zvolte **F5** klíč ke spuštění aplikace.  
  
     Aplikace je kompilována a pak se jeho funkce nasazují na server SharePoint a aktivují.  
  
3.  Na panelu rychlou navigaci, zvolte **pacientů** odkazu zobrazíte **pacientů** seznamu.  
  
     Názvy sloupců v seznamu by měly odpovídat těm, které jste zadali na **zobrazení** kartu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Zvolte **přidat novou položku** odkaz můžete vytvořit kartu s informacemi o pacientech.  
  
5.  Zadejte informace do polí a klikněte na tlačítko **Uložit** tlačítko.  
  
     Nový záznam se zobrazí v seznamu.  
  
## <a name="see-also"></a>Viz také:
 [Vytváření sloupců webu, typů obsahu a seznamů pro službu SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Postupy: vytvoření vlastního pole typu](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Typy obsahu](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Sloupce](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
