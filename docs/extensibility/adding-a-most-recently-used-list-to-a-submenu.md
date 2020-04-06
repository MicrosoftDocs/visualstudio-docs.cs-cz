---
title: Přidání naposledy použitého seznamu do podnabídky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740297"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Přidání naposledy použitého seznamu do podnabídky
Tento návod vychází z ukázek v [části Přidat podnabídku do nabídky](../extensibility/adding-a-submenu-to-a-menu.md)a ukazuje, jak přidat dynamický seznam do podnabídky. Dynamický seznam tvoří základ pro vytvoření seznamu naposledy použitých (MRU).

Dynamický seznam nabídek začíná zástupným symbolem v nabídce. Pokaždé, když je zobrazena nabídka, Visual Studio integrované vývojové prostředí (IDE) požádá VSPackage pro všechny příkazy, které by měly být zobrazeny na zástupný symbol. Dynamický seznam může nastat kdekoli v nabídce. Dynamické seznamy jsou však obvykle uloženy a zobrazeny samy o sobě v podnabídkách nebo v dolní části nabídek. Pomocí těchto návrhových vzorů povolíte dynamické mušce příkazů pro rozbalení a smršťování bez ovlivnění umístění jiných příkazů v nabídce. V tomto návodu je dynamický seznam OBJEKTU řízení o obrazových oknech zobrazen v dolní části existující podnabídky, která je oddělena od zbytku podnabídky čárou.

Technicky lze dynamický seznam použít také na panel nástrojů. Doporučujeme však, aby použití, protože panel nástrojů by měl zůstat beze změny, pokud uživatel provede konkrétní kroky ke změně.

Tento návod vytvoří seznam NAPOSLEDY DIčna čtyři položky, které změní své pořadí pokaždé, když je vybrána jedna z nich (vybraná položka se přesune na začátek seznamu).

Další informace o nabídkách a *souborech VSCT naleznete v* [tématu Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Požadavky
Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Vytvoření rozšíření

- Postupujte podle postupů v [přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md) k vytvoření podnabídky, která je upravena v následujících postupech.

  Postupy v tomto návodu předpokládají, že název `TopLevelMenu`balíčku VSPackage je , což je název, který se používá v [nabídce Přidat nabídku na řádek nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Vytvoření příkazu seznamu dynamických položek

1. Otevřete *soubor TestCommandPackage.vsct*.

2. V `Symbols` části v `GuidSymbol` uzlu s názvem guidTestCommandPackageCmdSet přidejte `MRUListGroup` symbol `cmdidMRUList` pro skupinu a příkaz, následujícím způsobem.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. V `Groups` části přidejte deklarovanou skupinu za existující položky skupiny.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. V `Buttons` části přidejte uzel představující nově deklarovaný příkaz za existující položky tlačítka.

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

    Příznak `DynamicItemStart` umožňuje příkaz, který má být generován dynamicky.

5. Sestavení projektu a spuštění ladění otestovat zobrazení nového příkazu.

    V nabídce **TestMenu** klepněte na novou podnabídku **Dílčí nabídka**, chcete-li zobrazit nový příkaz **Zástupný symbol MRU**. Po dynamické mdc seznam příkazů je implementována v dalším postupu, tento popisek příkazu bude nahrazen tímto seznamem při každém otevření podnabídky.

## <a name="filling-the-mru-list"></a>Vyplnění seznamu MRU

1. V *TestCommandPackageGuids.cs*přidejte následující řádky za existující ID příkazů v definici třídy. `TestCommandPackageGuids`

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. V *TestCommand.cs* přidejte následující příkaz using.

    ```csharp
    using System.Collections;
    ```

3. Přidejte následující kód do konstruktoru TestCommand po posledním volání AddCommand. Bude `InitMRUMenu` definována později

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Přidejte následující kód do třídy TestCommand. Tento kód inicializuje seznam řetězců, které představují položky, které mají být zobrazeny v seznamu MRU.

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

5. Po `InitializeMRUList` metodě přidejte metodu. `InitMRUMenu` Tím se inicializují příkazy nabídky seznamu MRU.

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

    Je nutné vytvořit objekt příkazu nabídky pro každou možnou položku v seznamu mru. IDE volá `OnMRUQueryStatus` metodu pro každou položku v seznamu MRU, dokud neexistují žádné další položky. Ve spravovaném kódu je jediným způsobem, jak ide vědět, že neexistují žádné další položky je nejprve vytvořit všechny možné položky. Pokud chcete, můžete označit další položky jako `mc.Visible = false;` neviditelné nejprve pomocí po vytvoření příkazu nabídky. Tyto položky pak mohou být `mc.Visible = true;` viditelné `OnMRUQueryStatus` později pomocí metody.

6. Po `InitMRUMenu` metodě přidejte `OnMRUQueryStatus` následující metodu. Toto je obslužná rutina, která nastaví text pro každou položku MRU.

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

7. Po `OnMRUQueryStatus` metodě přidejte `OnMRUExec` následující metodu. Toto je obslužná rutina pro výběr položky MRU. Tato metoda přesune vybranou položku na začátek seznamu a poté zobrazí vybranou položku v poli se zprávou.

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

## <a name="testing-the-mru-list"></a>Testování seznamu MRU

1. Sestavení projektu a začít ladění.

2. V nabídce **TestMenu** klepněte na tlačítko **Vyvolat příkaz TestCommand**. Tím se zobrazí okno se zprávou, která označuje, že byl vybrán příkaz.

    > [!NOTE]
    > Tento krok je nutné vynutit VSPackage načíst a správně zobrazit seznam MRU. Pokud tento krok přeskočíte, seznam MRU se nezobrazí.

3. V nabídce **Nabídka Test** klepněte na **položku Dílčí nabídka**. Seznam čtyř položek se zobrazí na konci podnabídky pod oddělovačem. Když klepnete na **položku 3**, mělo by se zobrazit okno se zprávou a zobrazit text **Vybraná položka 3**. (Pokud není zobrazen seznam čtyř položek, ujistěte se, že jste postupovali podle pokynů v předchozím kroku.)

4. Znovu otevřete podnabídku. Všimněte si, že **položka 3** je nyní v horní části seznamu a ostatní položky byly posunuty dolů o jednu pozici. Klepněte znovu na **položku 3** a všimněte si, že v poli se zprávou se stále zobrazuje **vybraná položka 3**, což znamená, že text byl správně přesunut na novou pozici spolu s popiskem příkazu.

## <a name="see-also"></a>Viz také
- [Dynamické přidávání položek nabídky](../extensibility/dynamically-adding-menu-items.md)
