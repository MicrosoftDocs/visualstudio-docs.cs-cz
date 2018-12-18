---
title: Přidání naposledy použité do podnabídky seznamu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 47
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87e9fb6ec0b4d0339427175fd18fdb79f6ef500b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744354"
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Přidání seznamu Naposledy použité do podnabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod vychází z ukázky v [přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md)a ukazuje, jak přidat dynamický seznam do podnabídky. V seznamu dynamického tento balíček je základem pro vytvoření seznamu naposledy (použitých).  
  
 Dynamická nabídka seznamu začíná zástupný symbol v nabídce. Pokaždé, když se zobrazí v nabídce, integrovaného vývojového prostředí (IDE) sady Visual Studio vyzve sady VSPackage pro všechny příkazy, které se mají zobrazit na zástupný symbol. Dynamický seznam se může nacházet kdekoli v nabídce. Dynamické seznamy jsou však obvykle ukládají a zobrazí samy o sobě z podnabídky nebo na dolním okraji nabídek. Když použijete tyto způsoby návrhu, povolíte dynamické seznam příkazů, tím rozbalíte a smlouvy, aniž by to ovlivnilo pozice dalších příkazů v nabídce. V tomto podrobném návodu zobrazí se v dolní části existující podnabídky, oddělené od zbytku podnabídky řádku dynamického seznamu naposledy použitých.  
  
 Seznam dynamického technicky, lze také použít na panelu nástrojů. Ale jsme Zabraňte tohle využívání, protože panelu nástrojů zůstanou beze změny, pokud uživatel provede určité kroky ho změnit.  
  
 Tento návod vytvoří seznam naposledy použitých čtyři položek, které se mění jejich pořadí pokaždé, když je vybrána, že jedna z nich (vybrané položky se přesune do horní části seznamu).  
  
 Další informace o nabídkách a soubory .vsct najdete v tématu [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Vytvoření rozšíření  
  
- Postupujte podle pokynů v [přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md) Vytvoření podnabídky, která se mění v následujících postupech.  
  
  V postupech v tomto názorném postupu se předpokládá, že je název sady VSPackage `TopLevelMenu`, což je název, který se používá v [přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Vytváření dynamických položek seznamu příkazu  
  
1.  Open TestCommandPackage.vsct.  
  
2.  V `Symbols` sekci `GuidSymbol` symbol pro uzel s názvem guidTestCommandPackageCmdSet, přidat `MRUListGroup` skupiny a `cmdidMRUList` příkaz následujícím způsobem.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  V `Groups` části, přidejte skupinu deklarovaný po existující položky skupiny.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  V `Buttons` části, přidejte uzel k reprezentaci příkazu nově deklarovaný po existující položky tlačítko.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart` Příznak umožňuje příkazu generována dynamicky.  
  
5.  Projekt sestavit a spustit ladění k testování zobrazení nového příkazu.  
  
     Na **TestMenu** nabídky, klikněte na nové podnabídky **podnabídka**, chcete-li zobrazit nový příkaz **zástupný symbol seznamu naposledy použitých položek**. Po dokončení implementace dynamického seznamu naposledy použitých příkazů v dalším postupu, tento příkaz Popisek se nahradí seznamu pokaždé, když je otevřen v podnabídce.  
  
## <a name="filling-the-mru-list"></a>Vyplnění seznamu naposledy použitých  
  
1.  V TestCommandPackageGuids.cs, přidejte následující řádky za existující identifikátory příkazů v `TestCommandPackageGuids` definici třídy.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  V souboru TestCommand.cs přidejte následující příkaz using.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Přidejte následující kód v konstruktoru TestCommand po posledním volání AddCommand. `InitMRUMenu` Bude obsahovat definici později  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Přidejte následující kód ve třídě TestCommand. Tento kód inicializuje seznam řetězců, které představují položky, které chcete zobrazit v seznamu naposledy použitých.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  Po `InitializeMRUList` metodu, přidejte `InitMRUMenu` metody. To inicializuje seznamu naposledy použitých položek seznamu příkazů.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     V seznamu naposledy použitých musíte vytvořit objekt příkazu nabídky pro každou položku je to možné. Volání rozhraní IDE `OnMRUQueryStatus` metoda pro každou položku v seznamu naposledy použitých, dokud nebyly nalezeny žádné další položky. Ve spravovaném kódu je nejprve vytvořte všechny možné položky jedině pro integrované vývojové prostředí vědět, že neexistují žádné další položky. Pokud chcete, můžete označit další položky jako nejsou viditelné v prvním pomocí `mc.Visible = false;` po vytvoření příkazu nabídky. Tyto položky můžete pak nastavena jako viditelná později pomocí `mc.Visible = true;` v `OnMRUQueryStatus` metody.  
  
6.  Po `InitMRUMenu` metodu, přidejte následující `OnMRUQueryStatus` metody. To je obslužná rutina, která nastaví text pro každou položku seznamu naposledy použitých položek.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Po `OnMRUQueryStatus` metodu, přidejte následující `OnMRUExec` metody. To je obslužná rutina pro výběr položky seznamu naposledy použitých položek. Tato metoda Přesune vybrané položky nahoru v seznamu a potom v okně se zprávou zobrazí vybranou položku.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>Testování do seznamu naposledy použitých  
  
#### <a name="to-test-the-mru-menu-list"></a>K otestování seznamu naposledy použité položky nabídky  
  
1.  Projekt sestavit a spustit ladění  
  
2.  Na **TestMenu** nabídky, klikněte na tlačítko **vyvolat TestCommand**. Tím se zobrazí okno se zprávou, která označuje, že jste vybrali příkazu.  
  
    > [!NOTE]
    >  Tento krok je nutný k vynucení balíčku VSPackage pro načtení a správné zobrazení seznamu naposledy použitých. Pokud tento krok přeskočíte, se nezobrazí seznam naposledy použitých položek.  
  
3.  Na **nabídka testu** nabídky, klikněte na tlačítko **podnabídka**. Zobrazí se seznam čtyři položky na konci podnabídky pod oddělovačem. Po kliknutí na **3 položky**, okno se zprávou by měla objevit a zobrazit text "Vybraná položka 3". (Pokud se nezobrazí seznam čtyři položky, ujistěte se, že jste postupovali podle pokynů v dřívějším kroku.)  
  
4.  Otevřete podnabídku znovu. Všimněte si, že **3 položky** je teď v horní části seznamu a ostatní položky byly nahrány o jednu pozici dolů. Klikněte na tlačítko **3 položky** znovu a Všimněte si, že do pole zpráva stále zobrazuje "Vybraná položka 3", která označuje, že text má správně přesunuta do nového umístění společně s popisek příkazu.  
  
## <a name="see-also"></a>Viz také  
 [Dynamické přidávání položek nabídky](../extensibility/dynamically-adding-menu-items.md)

