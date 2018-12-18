---
title: Přidání Kontroleru nabídky do panelu nástrojů | Dokumentace Microsoftu
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
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13dec4b907b52e35b5b2377aafa511e50dc5cc48
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771538"
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Přidání kontroleru nabídky do panelu nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod vychází [přidání panelu nástrojů do panelu nástrojů](../extensibility/adding-a-toolbar-to-a-tool-window.md) návod a ukazuje, jak přidat kontroleru nabídky do panelu nástrojů okno nástrojů. Zde uvedených kroků můžete použít také na panel nástrojů, který je vytvořen v [přidání panelu nástrojů](../extensibility/adding-a-toolbar.md) návodu.  
  
 Kontroleru nabídky je ovládací prvek rozdělení. Levé straně kontroleru nabídky zobrazí příkaz poslední použitá a ji můžete spustit tak, že na něj kliknete. Pravé straně kontroleru nabídky je šipka, při kliknutí otevře seznam dalších příkazů. Když kliknete na příkaz v seznamu spuštění příkazu a nahrazuje příkaz na levé straně kontroleru nabídky. Tímto způsobem kontroleru nabídky funguje stejně jako příkazové tlačítko, které vždy zobrazí poslední použitá příkaz ze seznamu.  
  
 Nabídka řadiče se může objevit v nabídkách, ale se nejčastěji používají na panely nástrojů.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Vytvoření Kontroleru nabídky  
  
#### <a name="to-create-a-menu-controller"></a>Vytvoření kontroleru nabídky  
  
1. Postupujte podle postupů popsaných v [přidání panelu nástrojů do panelu nástrojů](../extensibility/adding-a-toolbar-to-a-tool-window.md) vytvořit panel nástrojů s panelem nástrojů.  
  
2. V TWTestCommandPackage.vsct přejděte do části symboly. V guidsymbol – element s názvem **guidTWTestCommandPackageCmdSet**, deklarujte kontroler vaší nabídky, skupina kontroleru nabídky a tři položky nabídky.  
  
   ```xml  
   <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
   ```  
  
3. V části nabídky po poslední položka nabídky definujte jako nabídka kontroleru nabídky.  
  
   ```xml  
   <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <CommandFlag>TextChanges</CommandFlag>  
       <CommandFlag>TextIsAnchorCommand</CommandFlag>  
       <Strings>  
           <ButtonText>Test Menu Controller</ButtonText>  
           <CommandName>Test Menu Controller</CommandName>  
       </Strings>  
   </Menu>  
   ```  
  
    `TextChanges` a `TextIsAnchorCommand` příznaky musí být zahrnut umožňuje kontroleru nabídky tak, aby odrážely posledních vybraný příkaz.  
  
4. Ve skupinách části po poslední záznam skupiny přidáte skupinu nabídek kontroleru.  
  
   ```xml  
   <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
   </Group>  
   ```  
  
    Nastavením kontroleru nabídky jako nadřazený všechny příkazy umístěn v této skupině se zobrazí v kontroleru nabídky. `priority` Atribut je vynechán, který nastaví na výchozí hodnotu 0, protože budou skupiny jenom na kontroleru nabídky.  
  
5. V části tlačítka po poslední položka tlačítko přidáte element přepínače pro každou z položek nabídky.  
  
   ```xml  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPic1" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 1</ButtonText>  
           <CommandName>MC Item 1</CommandName>  
       </Strings>  
   </Button>  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPic2" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 2</ButtonText>  
           <CommandName>MC Item 2</CommandName>  
       </Strings>  
   </Button>  
   <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
       <Icon guid="guidImages" id="bmpPicSearch" />  
       <CommandFlag>IconAndText</CommandFlag>  
       <Strings>  
           <ButtonText>MC Item 3</ButtonText>  
           <CommandName>MC Item 3</CommandName>  
       </Strings>  
   </Button>  
   ```  
  
6. V tomto okamžiku můžete si prohlédnout kontroleru nabídky. Sestavte projekt a spusťte ladění. Měli byste vidět experimentální instanci aplikace.  
  
   1. Na **zobrazení / ostatní Windows** nabídce otevřete **testovací třídy ToolWindow**.  
  
   2. Kontroleru nabídky se zobrazí na panelu nástrojů v okně nástroje.  
  
   3. Klikněte na šipku na pravé straně kontroleru nabídky se zobrazí tři možné příkazy.  
  
      Všimněte si, že po kliknutí na příkaz, názvu kontroleru nabídky mění k zobrazení tohoto příkazu. V další části přidáme kód pro aktivaci těchto příkazů.  
  
## <a name="implementing-the-menu-controller-commands"></a>Implementace příkazy Kontroleru nabídky  
  
1.  V TWTestCommandPackageGuids.cs přidejte po příkazu existující identifikátory ID příkazu pro vaše položky nabídky tři.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  V TWTestCommand.cs přidejte následující kód v horní části třídy TWTestCommand.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  V konstruktoru TWTestCommand po posledním volání `AddCommand` metodu, přidejte kód pro směrování událostí pro každý příkaz prostřednictvím stejné obslužné rutiny.  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Přidejte obslužnou rutinu události do třídy TWTestCommand Označit vybrané příkazu, kontrolovaný.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Přidáte obslužnou rutinu události, která zobrazí prvek MessageBox, když uživatel vybere příkaz na kontroleru nabídky:  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>Testování Kontroleru nabídky  
  
1.  Sestavte projekt a spusťte ladění. Měli byste vidět experimentální instanci aplikace.  
  
2.  Otevřít **testovací třídy ToolWindow** na **zobrazení / ostatní Windows** nabídky.  
  
     Kontroleru nabídky se zobrazí na panelu nástrojů v okně nástroje a zobrazí **MC položka 1**.  
  
3.  Klikněte na tlačítko kontroleru nabídky na levé straně na šipku.  
  
     Měli byste vidět tři položky se vybere první z nich a má pole zvýraznění kolem jeho ikonu. Klikněte na tlačítko **MC položky 3**.  
  
     Zobrazí se dialogové okno se zprávou **vyberete kontroleru nabídky 3 položky**. Všimněte si, že zpráva odpovídá text na tlačítku kontroleru nabídky. Tlačítko nabídky řadiče se teď zobrazují **3 položky MC**.  
  
## <a name="see-also"></a>Viz také  
 [Přidání panelu nástrojů do panelu nástrojů](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Přidání panelu nástrojů](../extensibility/adding-a-toolbar.md)

