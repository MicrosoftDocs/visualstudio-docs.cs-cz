---
title: 'Postupy: označení ovládacích prvků jako bezpečných ovládacích prvků | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd7ed13504d3d91f4239a8ea070454e1c31b1114
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016253"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Postupy: označení ovládacích prvků jako bezpečných ovládacích prvků
  Z důvodu zabezpečení rozlišuje SharePoint mezi webovými ovládacími prvky, které jsou chráněny proti vkládání skriptu a webovým ovládacím prvkům, které nejsou. K chráněným ovládacím prvkům nebo *bezpečným ovládacím prvkům*může mít přístup nedůvěryhodní uživatelé. Ovládací prvky lze označit jako bezpečné v vlastnosti položky projektu služby SharePoint nebo v **Návrháři balíčku** při přidání sestavení do balíčku. Další informace najdete v tématu

- [web.config nastavení souboru se změní](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) a [registruje sestavení webové části jako bezpečný ovládací prvek](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

> [!IMPORTANT]
> Tyto postupy jsou pro ilustrativní účely. Označte ovládací prvky bezpečně pouze v případě, že jste si jisti, že jsou zabezpečené.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Označení bezpečných ovládacích prvků ve vlastnosti položky bezpečných ovládacích prvků

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Označení ovládacích prvků jako bezpečných nebo nebezpečných ve vlastnosti položky bezpečného řízení

1. Vytvořte řešení služby SharePoint pomocí projektu vizuální webové části.

2. Přidejte do webové části dva ovládací prvky: textové pole a tlačítko. Ponechte názvy na jejich výchozích hodnotách: TextBox1 a Button1, v uvedeném pořadí.

3. Přidejte dvě položky do vlastnosti **položky bezpečného řízení** webové části. Chcete-li to provést, klikněte na tlačítko se třemi tečkami (![elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) vedle vlastnosti **položky bezpečné řízení** v okně **vlastnosti** .

     Zobrazí se dialogové okno **položky bezpečného řízení** .

4. V dialogovém okně **položky bezpečného řízení** klikněte dvakrát na tlačítko **Přidat** a přidejte dvě položky bezpečného řízení do podokna **Členové** : jeden pro tlačítko a druhý pro textové pole.

5. Zvolte první položku bezpečného řízení a pak změňte hodnotu vlastnosti **Safe** na **false**, vlastnost **název typu** na **Button1**a její vlastnost **Safe** na **hodnotu false**.

     Tento krok určuje ovládací prvek tlačítko jako nezabezpečený ovládací prvek.

6. V seznamu vyberte druhou položku bezpečného řízení. Ponechte hodnotu vlastnosti **Safe** nastavenou na **true** a jako vlastnost **název typu** nastavte parametr **TextBox1** a jeho vlastnost **Safe proti skriptu** na **hodnotu true**.

     Ovládací prvek textové pole je nyní označen jako ovládací prvek, který je bezpečný proti injektáže skriptu.

7. Kliknutím na tlačítko **OK** zavřete dialogové okno.

## <a name="marking-safe-controls-in-the-package-designer"></a>Označení bezpečných ovládacích prvků v Návrháři balíčků

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Označení ovládacích prvků jako bezpečných nebo nebezpečných v Návrháři balíčků

1. Vytvořte řešení služby SharePoint pomocí projektu vizuální webové části.

2. Přidejte do webové části dva ovládací prvky: textové pole a tlačítko. Ponechte názvy na jejich výchozích hodnotách: TextBox1 a Button1, v uvedeném pořadí.

     Poznamenejte si obor názvů ovládacího prvku, protože je použit později.

3. Na panelu nabídek vyberte sestavit sestavení **Build**  >  **řešení** a sestavte projekt.

4. Vytvořte další řešení SharePoint.

5. V **Průzkumník řešení**otevřete místní nabídku pro soubor *Package. Package* a pak zvolte **otevřít** . otevře se **Návrhář balíčku**.

6. V **Návrháři balíčků**klikněte na kartu **Upřesnit** .

7. V části **Další sestavení**zvolte tlačítko **Přidat** a poté ze seznamu zvolte možnost **Přidat existující sestavení** .

8. V dialogovém okně **Přidat existující sestavení** klikněte na tlačítko se třemi tečkami (![Elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) vedle **cesty ke zdroji**.

9. Zvolte sestavení z řešení služby SharePoint, které jste vytvořili v kroku 1, a poté klikněte na tlačítko **otevřít** .

10. V tomto příkladu ponechte možnost **cíl nasazení** jako GlobalAssemblyCache.

     Tento krok způsobí, že sestavení bude nasazeno do globální mezipaměti sestavení (GAC) systému. Pokud chcete, aby sestavení bylo nasazeno do složky webové aplikace (bin), vyberte místo toho tuto možnost. Další informace najdete v tématu [nasazení webové části ve službě SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

11. V poli **bezpečné ovládací prvky** vyberte **kliknutím sem tlačítko Přidat novou položku** .

12. Zadejte hodnoty vlastností z následující tabulky.

    |Název vlastnosti|Hodnota|
    |-------------------|-----------|
    |Obor názvů|Plně kvalifikovaný obor názvů pro ovládací prvek, například **BdcModelProject1. VisualWebPart1**.|
    |Název typu|Tlačítk|
    |Název sestavení|Silný název sestavení, například: Microsoft. Office. SharePoint. ClientExtensions, verze = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Odvod|Zrušte zaškrtnutí políčka **bezpečné** .|
    |Bezpečné proti skriptu|Zrušte zaškrtnutí políčka **bezpečné proti skriptu** .|

    > [!NOTE]
    > Hodnota **názvu sestavení** pro sestavení přidaná prostřednictvím karty **Upřesnit** v **Návrháři balíčku** nemůže být token, musí se jednat o sestavení se silným názvem. Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Chcete-li vytvořit další položku bezpečného řízení, vyberte klávesu **TAB** .

14. Klikněte na tlačítko **pro přidání nové položky znovu kliknutím sem** .

15. Zadejte hodnoty vlastností z následující tabulky.

    |Název vlastnosti|Hodnota|
    |-------------------|-----------|
    |Obor názvů|Plně kvalifikovaný obor názvů pro ovládací prvek, například **BdcModelProject1. VisualWebPart1**.|
    |Název typu|TextBox1|
    |Název sestavení|Silný název sestavení, například: Microsoft. Office. SharePoint. ClientExtensions, verze = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Odvod|Zaškrtněte políčko **bezpečné** .|
    |Bezpečné proti skriptu|Zaškrtněte políčko **bezpečné proti skriptu** .|

16. Zvolte klávesu **TAB** a potom kliknutím na tlačítko **OK** zavřete dialogové okno.

## <a name="see-also"></a>Viz také:
- [Poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
