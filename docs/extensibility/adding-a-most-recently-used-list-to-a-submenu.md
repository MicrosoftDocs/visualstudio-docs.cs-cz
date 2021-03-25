---
title: Přidání seznamu naposledy použitých do podnabídky | Microsoft Docs
description: Naučte se, jak přidat dynamický seznam obsahující naposledy použité příkazy nabídky do podnabídky v integrovaném vývojovém prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb238afb0f583f1b913fbd87f4f50e43679ebd7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060013"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Přidat seznam naposledy použitých do podnabídky
Tento názorný postup se sestavuje v předváděních v [nabídce Přidat podnabídku do nabídky](../extensibility/adding-a-submenu-to-a-menu.md)a ukazuje, jak přidat dynamický seznam do podnabídky. Dynamický seznam tvoří základ pro vytvoření seznamu naposledy použitých položek.

Dynamický seznam nabídek začíná zástupným symbolem v nabídce. Pokaždé, když se zobrazí nabídka, integrované vývojové prostředí (IDE) sady Visual Studio požádá VSPackage o všechny příkazy, které by se měly zobrazit na zástupném symbolu. Dynamický seznam se může nacházet kdekoli v nabídce. Dynamické seznamy jsou však obvykle uloženy a zobrazeny v podnabídkách nebo v dolních seznamech nabídek. Pomocí těchto vzorů návrhu povolíte dynamický seznam příkazů pro rozšíření a kontrakt, aniž by to mělo vliv na pozici dalších příkazů v nabídce. V tomto návodu se dynamický seznam MRU zobrazuje v dolní části existující podnabídky, která je oddělená od zbytku podnabídky o řádek.

Technicky, na panelu nástrojů lze také použít dynamický seznam. Omlouváme se ale za použití, protože panel nástrojů by neměl zůstat beze změny, pokud uživatel neprovede konkrétní kroky ke změně.

Tento návod vytvoří seznam naposledy použitých položek se čtyřmi položkami, které změní jejich pořadí pokaždé, když je vybraná jedna z nich (vybraná položka se přesune na začátek seznamu).

Další informace o nabídkách a souborech *. vsct* naleznete v tématech [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Požadavky
Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Vytvořit rozšíření

- Podle pokynů v části [Přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md) vytvořte podnabídku, která je upravena v následujících postupech.

  Postupy v tomto návodu předpokládají, že název VSPackage je `TestCommand` , což je název, který se používá v [Přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Vytvoření dynamického seznamu položek – příkaz

1. Otevřete *TestCommandPackage. vsct*.

2. V `Symbols` části v `GuidSymbol` uzlu s názvem guidTestCommandPackageCmdSet přidejte symbol pro `MRUListGroup` skupinu a `cmdidMRUList` příkaz, a to následujícím způsobem.

    ```xml
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. V `Groups` části přidejte deklarovanou skupinu za existující položky skupiny.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

4. V `Buttons` části přidejte uzel představující nově deklarovaný příkaz za existující položky tlačítka.

    ```xml
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

    `DynamicItemStart`Příznak umožňuje dynamické vygenerování příkazu.

5. Sestavte projekt a spusťte ladění pro otestování zobrazení nového příkazu.

    V nabídce **TestMenu** klikněte na novou **podnabídku** a zobrazte nový **zástupný symbol MRU**. Po implementaci dynamického seznamu příkazů v dalším postupu bude popisek tohoto příkazu nahrazen tímto seznamem pokaždé, když je podnabídka otevřena.

## <a name="filling-the-mru-list"></a>Naplnění seznamu naposledy použitých

1. V *TestCommandPackageGuids. cs* přidejte následující řádky za existující identifikátory příkazů v `TestCommandPackageGuids` definici třídy.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. V *TestCommand. cs* přidejte následující příkaz using.

    ```csharp
    using System.Collections;
    ```

3. Přidejte následující kód do konstruktoru TestCommand po posledním volání použijete AddCommand menucommandsetgui. `InitMRUMenu`Bude definováno později.

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Do třídy TestCommand přidejte následující kód. Tento kód inicializuje seznam řetězců, které reprezentují položky, které se mají zobrazit v seznamu naposledy použitých položek.

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

5. Za `InitializeMRUList` metodu přidejte `InitMRUMenu` metodu. Tím se inicializuje příkazy nabídky seznamu naposledy použitých položek.

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

    Je nutné vytvořit objekt příkazu nabídky pro každou možnou položku v seznamu naposledy použitých položek. Rozhraní IDE volá `OnMRUQueryStatus` metodu pro každou položku v seznamu MRU, dokud neexistují žádné další položky. Ve spravovaném kódu je jediným způsobem, jak rozhraní IDE ví, že neexistují žádné další položky, je nejdříve vytvořit všechny možné položky. Pokud chcete, můžete označit další položky jako neviditelné jako první pomocí `mc.Visible = false;` po vytvoření příkazu nabídky. Tyto položky lze následně zobrazit později pomocí `mc.Visible = true;` `OnMRUQueryStatus` metody v metodě.

6. Za `InitMRUMenu` metodu přidejte následující `OnMRUQueryStatus` metodu. Toto je obslužná rutina, která nastavuje text pro každou naposledy použitou položku.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Za `OnMRUQueryStatus` metodu přidejte následující `OnMRUExec` metodu. Toto je obslužná rutina pro výběr naposledy použité položky. Tato metoda přesune vybranou položku na začátek seznamu a potom zobrazí vybranou položku v okně se zprávou.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
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

## <a name="testing-the-mru-list"></a>Testování seznamu naposledy použitých položek

1. Sestavte projekt a spusťte ladění.

2. V nabídce **TestMenu** klikněte na **vyvolat TestCommand**. Tím se zobrazí okno se zprávou, které indikuje, že byl příkaz vybrán.

    > [!NOTE]
    > Tento krok je nutný k vynucení načtení a správnému zobrazení seznamu naposledy použitých pro VSPackage. Pokud tento krok přeskočíte, nezobrazuje se seznam naposledy použitých položek.

3. V nabídce **Nabídka testu** klikněte na **dílčí nabídka**. Na konci podnabídky se zobrazí seznam čtyř položek pod oddělovačem. Když kliknete na **položku 3**, zobrazí se okno se zprávou a zobrazí se text, **Vybraná položka 3**. (Pokud se seznam čtyř položek nezobrazí, ujistěte se, že jste postupovali podle pokynů v předchozím kroku.)

4. Znovu otevřete podnabídku. Všimněte si, že **položka 3** je nyní na začátku seznamu a ostatní položky byly posunuty o jednu pozici. Klikněte na **položku 3** znovu a Všimněte si, že se v okně se zprávou stále zobrazuje **Vybraná položka 3**, která indikuje, že se text správně přesunul do nové pozice spolu s popiskem příkazu.

## <a name="see-also"></a>Viz také
- [Dynamické přidávání položek nabídky](../extensibility/dynamically-adding-menu-items.md)
