---
title: Vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint
titleSuffix: ''
description: V tomto návodu vytvořte vlastní sloupec webu (pole), vlastní typ obsahu, který používá sloupec lokality, a seznam, který používá typ obsahu v SharePointu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d205203797d8bd50c7b3132df86fbff9dbad1771
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937690"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint
  Následující postupy ukazují, jak vytvořit vlastní sloupce webu služby SharePoint (nebo *pole*) a také typ obsahu, který používá sloupce lokality. Také ukazuje, jak vytvořit seznam, který používá nový typ obsahu.

 Tento návod zahrnuje následující úlohy:

- [Vytváření vlastních sloupců webu](#create-custom-site-columns).

- [Vytvořte vlastní typ obsahu](#create-a-custom-content-type).

- [Vytvoří seznam](#create-a-list).

- [Otestujte aplikaci](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Windows a SharePointu.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Vytváření vlastních sloupců webu
 Tento příklad vytvoří seznam pro správu pacientů v nemocnici. Nejprve je třeba vytvořit projekt služby SharePoint v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a přidat do něj sloupce webu, a to následujícím způsobem.

#### <a name="to-create-the-project"></a>Vytvoření projektu

1. V nabídce [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **soubor** klikněte na příkaz **Nový**  >  **projekt**.
::: moniker range="=vs-2017"
2. V dialogovém okně **Nový projekt** v části **Visual C#** nebo **Visual Basic** rozbalte uzel **Office/SharePoint** a pak vyberte **řešení SharePoint**.

3. V podokně **šablony** vyberte **prázdný projekt SharePoint** pro konkrétní verzi SharePointu, kterou jste nainstalovali. Například pokud máte SharePoint 2016 nainstalovat, vyberte šablonu **projektu SharePoint 2016-Empty** .  

4. Změňte název projektu na **Clinic** a pak klikněte na tlačítko **OK** .

5. V dialogovém okně **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte adresu URL místního webu služby SharePoint, ke kterému chcete přidat novou položku vlastního pole, nebo použijte výchozí umístění ( `http://<` *systémový systém*) `>/)` .

6. V části **co je úroveň důvěryhodnosti pro toto řešení služby SharePoint?** použijte výchozí hodnotu **nasadit jako řešení v izolovaném prostoru (sandbox)**.

     Další informace o řešeních v izolovaném prostoru a řešeních farmy najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

7. Klikněte na tlačítko **Dokončit** . Projekt je nyní uveden v **Průzkumník řešení**.
::: moniker-end
::: moniker range=">=vs-2019"
2.  V dialogovém okně **vytvořit nový projekt** vyberte **prázdný projekt SharePoint** pro konkrétní verzi SharePointu, kterou jste nainstalovali. Například pokud máte SharePoint 2016 nainstalovat, vyberte šablonu **projektu SharePoint 2016-Empty** .
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Změňte název projektu na **Clinic** a pak klikněte na tlačítko **vytvořit** .

4. V dialogovém okně **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte adresu URL místního webu služby SharePoint, ke kterému chcete přidat novou položku vlastního pole, nebo použijte výchozí umístění ( `http://<` *systémový systém*) `>/)` .

5. V části **co je úroveň důvěryhodnosti pro toto řešení služby SharePoint?** použijte výchozí hodnotu **nasadit jako řešení v izolovaném prostoru (sandbox)**.

     Další informace o řešeních v izolovaném prostoru a řešeních farmy najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

6. Klikněte na tlačítko **Dokončit** . Projekt je nyní uveden v **Průzkumník řešení**.
::: moniker-end

#### <a name="to-add-site-columns"></a>Přidání sloupců webu

1. Přidá nový sloupec webu. To provedete tak, že v **Průzkumník řešení** kliknete pravým tlačítkem na projekt **Clinic** a pak zvolíte **Přidat**  >  **novou položku**.

2. V dialogovém okně **Přidat novou položku** zvolte **sloupec lokality**, změňte **název na jméno a potom** klikněte na tlačítko **Přidat** .

3. V souboru *Elements.xml* sloupce webu ponechte nastavení **typ** jako **text** a změňte nastavení **skupiny** na považovat **sloupce webu**. Po dokončení by soubor *Elements.xml* sloupce webu měl vypadat jako v následujícím příkladu.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="PatientName"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

    > [!TIP]
    > Pokud v názvu sloupce webu použijete ve stylu CamelCase velká a malá písmena, Visual Studio automaticky přidá mezeru do DisplayName.
    > Doporučujeme nepoužívat mezery v názvu sloupce webu, protože může způsobit problémy při pokusu o nasazení řešení do služby SharePoint.

4. Pomocí stejného postupu přidejte do projektu dva další sloupce webu: **PatientID** (Type = "Integer") a **Doctor** (Type = "text"). Nastavte jejich hodnotu Group na **clinice sloupce webu**.

## <a name="create-a-custom-content-type"></a>Vytvoření vlastního typu obsahu
 Dále vytvořte typ obsahu založený na typu obsahu kontakty – to zahrnuje sloupce webu, které jste vytvořili v předchozím postupu. Díky založení typu obsahu u stávajícího typu obsahu můžete ušetřit čas, protože základní typ obsahu poskytuje několik sloupců webu pro použití v novém typu obsahu.

#### <a name="to-create-a-custom-content-type"></a>Vytvoření vlastního typu obsahu

1. Přidejte do projektu typ obsahu. Chcete-li to provést, v **Průzkumník řešení** vyberte uzel projektu

2. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

3. V části **Visual C#** nebo **Visual Basic** rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

4. V podokně **šablony** zvolte šablonu **typ obsahu** , změňte název na **informace o pacientech** a pak klikněte na tlačítko **Přidat** .

     Otevře se **Průvodce přizpůsobením SharePointu** .

5. V seznamu **který základní typ obsahu by měl tento typ obsahu dědit ze** seznamu zvolte možnost **kontakt** jako typ obsahu, na kterém chcete vytvořit nový typ obsahu, a pak klikněte na tlačítko **Dokončit** .

     Díky tomu získáte přístup k dalším potenciálně užitečným sloupcům webu v typu obsahu kontaktu kromě sloupců, které jste definovali dříve.

6. Po zobrazení návrháře typu obsahu přidejte na kartě **sloupce** tři sloupce webu, které jste definovali dříve: **název pacienta**, **ID pacienta** a **název lékaře**. Chcete-li přidat tyto sloupce, zvolte první seznam v seznamu sloupce webu v části **Zobrazovaný název** a potom v seznamu vyberte každý sloupec lokalit v jednom.

    > [!TIP]
    > Chcete-li zvolit sloupce webu rychleji, vyfiltrujte seznam zadáním prvních několika písmen názvu sloupce.

7. Kromě tří vlastních sloupců webu přidejte sloupec **Komentáře** webu ze seznamu sloupce webu.

8. Zaškrtněte políčko **povinné** pro sloupce **název pacienta** a **ID pacienta** , aby byla povinná pole.

9. Na kartě **typ obsahu** se ujistěte, že název typu obsahu je **informace o pacientech**, a pak změňte popis na **kartu informace o pacientech**.

10. Změňte **název skupiny** na **Clinicd Content Types** a ostatní nastavení ponechte na jejich výchozích hodnotách.

11. V panelu **nabídek zvolte možnost**  >  **Uložit vše** a pak zavřete Návrhář typu obsahu.

## <a name="create-a-list"></a>Vytvoří seznam.
 Nyní vytvořte seznam, který používá nový typ obsahu a sloupce webu.

#### <a name="to-create-a-list"></a>Vytvoření seznamu

1. Přidejte do projektu seznam. Chcete-li to provést, v **Průzkumník řešení** vyberte uzel projektu.

2. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

3. V rámci **jazyka Visual C#** nebo **Visual Basic** rozbalte uzel **služby SharePoint** .

4. V podokně **šablony** zvolte šablonu **seznamu** , změňte název na **pacienty** a pak klikněte na tlačítko **Přidat** .

5. Ponechte **seznam přizpůsobit** podle nastavení **výchozí (vlastní seznam)** a pak klikněte na tlačítko **Dokončit** .

6. V Návrháři seznamu vyberte tlačítko **typy obsahu** a zobrazte tak dialogové okno **Nastavení typu obsahu** .

7. Zvolte nový řádek, v seznamu typů obsahu vyberte typ obsahu **informace o pacientech** a pak klikněte na tlačítko **OK** .

     Tím se do seznamu přidá všechny sloupce webu z typu obsahu **informace o pacientovi** .

8. Odstraňte všechny sloupce webu v seznamu s výjimkou následujících:

    - ID pacienta

    - Název pacienta

    - Telefon domů

    - E-Mail

    - Název lékaře

    - Komentáře

9. V části **Zobrazovaný název sloupce** vyberte prázdný řádek, přidejte vlastní sloupec seznamu a pojmenujte ho **nemocnice**. Jeho datový typ ponechte na **jeden řádek textu**.

     Sloupec vlastní seznam se vztahuje pouze na tento seznam. Když do seznamu přidáte sloupec vlastního seznamu, vytvoří se nový typ obsahu seznamu, včetně všech sloupců přidaných do seznamu, který se nastaví jako výchozí seznam.

    > [!TIP]
    > Zvolíte-li sloupec ze seznamu sloupců webu, bude použit existující sloupec webu. Pokud však zadáte hodnotu názvu sloupce bez výběru sloupců v seznamu, vytvoří se sloupec vlastní seznam, i když již v seznamu existuje sloupec se stejným názvem.

     Místo toho, abyste nastavili datový typ pro sloupec vlastní seznam na **jeden řádek textu**, můžete místo toho nastavit datový typ pro tento sloupec na vyhledávání a hodnoty by se načetly z tabulky nebo jiného seznamu. Informace o vyhledávacích sloupcích najdete v tématech [Seznam vztahů v sharepointu 2010](/previous-versions/msp-n-p/ff798514(v=pandp.10)) a [vyhledávání a seznam relací](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14)).

10. Vedle pole název **pacienta** a **název pacienta** zaškrtněte políčko **povinné** .

11. Na kartě **zobrazení** vyberte prázdný řádek a vytvořte zobrazení. Do sloupce **název zobrazení** zadejte **Podrobnosti o pacientech** v prázdném řádku.

     Na kartě **zobrazení** můžete zadat sloupce, které se mají zobrazit v seznamu SharePointu.

12. Zvolte nový řádek s **podrobnostmi o pacientech** a pak zvolte tlačítko **nastavit jako výchozí** .

     Nové zobrazení je nyní výchozím zobrazením seznamu.

13. Přidejte následující sloupce do seznamu **vybrané sloupce** v tomto pořadí:

    - ID pacienta

    - Název pacienta

    - Telefon domů

    - E-Mail

    - Název lékaře

    - Ústavní

    - Komentáře

14. V seznamu **vlastnosti** zvolte vlastnost **řazení a seskupování** a potom zvolte ![ikonu tří teček se třemi](../sharepoint/media/ellipsisicon.gif "Ikona se třemi tečkami") tečkami. zobrazí se dialogové okno **řazení a seskupování** .

15. V seznamu **název sloupce** zvolte **název pacienta**, ujistěte se, že sloupec **řazení** je nastavený na **vzestupné** a pak klikněte na tlačítko **OK** .

## <a name="test-the-application"></a>Testování aplikace
 Teď, když jsou vlastní sloupce webu, typ obsahu a seznam připravené, nasaďte je do SharePointu a spusťte aplikaci, která ji otestuje.

#### <a name="to-test-the-application"></a>Testování aplikace

1. V řádku nabídek vyberte **soubor**  >  **Uložit vše**.

2. Spusťte aplikaci kliknutím na klávesu **F5** .

     Aplikace je kompilována a poté jsou její funkce nasazeny do služby SharePoint a aktivovány.

3. Na panelu Rychlé navigace vyberte odkaz **pacienty** a zobrazte seznam **pacientů** .

     Názvy sloupců v seznamu se musí shodovat s názvy, které jste zadali na kartě **zobrazení** v části [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

4. Klikněte na odkaz **Přidat novou položku** a vytvořte kartu s informacemi o pacientech.

5. Do polí zadejte informace a pak klikněte na tlačítko **Uložit** .

     Nový záznam se zobrazí v seznamu.

## <a name="see-also"></a>Viz také
- [Vytváření sloupců webu, typů obsahu a seznamů pro službu SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Postupy: Vytvoření vlastního typu pole](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [Typy obsahu](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Sloupce](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
