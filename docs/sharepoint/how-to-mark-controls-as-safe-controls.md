---
title: 'Postupy: označení ovládacích prvků jako bezpečných | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 04470034f1fa1531a1677b4acd6b36f0b99c8a62
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120272"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Postupy: označení ovládacích prvků jako bezpečných ovládacích prvků
  Pro zabezpečení SharePoint rozlišuje webových ovládacích prvků, které jsou chráněny před vložení skriptu a webové ovládací prvky, které nejsou. Chráněné ovládací prvky, nebo *bezpečné ovládací prvky*, dostanete nedůvěryhodným uživatelům. Ovládací prvky jako bezpečné ve bezpečné položky řízení vlastnosti položky projektu služby SharePoint nebo v můžete označit **návrháře balíčků** při přidávání sestavení do balíčku. Další informace naleznete v tématu  
  
 [soubor Web.config Změna nastavení](http://go.microsoft.com/fwlink/?LinkId=178965) a [registrace sestavení webové části jako bezpečné ovládací prvek](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Tyto postupy jsou pro ilustraci. Označení ovládacích prvků bezpečné pouze v případě, že jste si jisti, že jsou zabezpečené.  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Označení bezpečné ovládací prvky ve vlastnosti položky bezpečné ovládací prvek  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>K označení ovládacích prvků jako bezpečných nebo unsafe ve vlastnosti položky bezpečné ovládací prvek
  
1.  Vytvořte řešení služby SharePoint s projektem Visual webové části.  
  
2.  Přidání dvou ovládacích prvků do webové části: textové pole a tlačítko. Ponecháte názvy na jejich výchozí hodnoty, TextBox1 a Button1.  
  
3.  Přidat dvě položky do webové části **bezpečné položky řízení** vlastnost. To pokud chcete udělat, zvolte se třemi tečkami (![ASP.NET – Návrhář mobilních řešení elipsy](../sharepoint/media/mwellipsis.gif "ASP.NET – Návrhář mobilních řešení elipsy")) vedle položky **bezpečné položky řízení** vlastnost  **Vlastnosti** okno.  
  
     **Bezpečné položky řízení** zobrazí se dialogové okno.  
  
4.  V **bezpečné položky řízení** dialogovém okně vyberte **přidat** tlačítko dvakrát přidáte dvě položky bezpečné řízení **členy** podokně: jeden pro tlačítko a jeden pro textové pole.  
  
5.  Vyberte první položka bezpečné řízení a poté změňte hodnotu jeho **bezpečné** vlastnost **False**, jeho **název typu** vlastnost **Button1**a jeho **skriptu bezpečné proti** vlastnost **False**.  
  
     Tento krok identifikuje ovládacího prvku tlačítko jako nezabezpečený ovládací prvek.  
  
6.  V seznamu vyberte druhý položka bezpečné řízení. Ponechte hodnotu jeho **bezpečné** vlastnost jako **True** a nastavit jeho **název typu** vlastnost **TextBox1** a jeho **bezpečné Proti skriptu** vlastnost **True**.  
  
     Textové pole je nyní označena jako ovládací prvek, který je bezpečný pro vložení skriptu.  
  
7.  Vyberte **OK** tlačítko dialogové okno zavřete.  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>Označení bezpečné ovládací prvky v návrháře balíčků  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>K označení ovládací prvky jako bezpečných nebo unsafe v návrháře balíčků
  
1.  Vytvořte řešení služby SharePoint s projektem Visual webové části.  
  
2.  Přidání dvou ovládacích prvků do webové části: textové pole a tlačítko. Ponecháte názvy na jejich výchozí hodnoty, TextBox1 a Button1.  
  
     Si poznamenejte obor názvů ovládacího prvku, protože je používán později.  
  
3.  Na řádku nabídek zvolte **sestavení** > **sestavit řešení** a tím projekt sestavit.  
  
4.  Vytvořte další řešení služby SharePoint.  
  
5.  V **Průzkumníku řešení**, otevřete místní nabídku pro *Package.Package* souboru a potom vyberte **otevřete** otevřete **návrháře balíčků**.  
  
6.  V **návrháře balíčků**, vyberte **Upřesnit** kartě.  
  
7.  V části **dalších sestavení**, vyberte **přidat** tlačítko a potom vyberte **přidat existující sestavení** ze seznamu.  
  
8.  V **přidat existující sestavení** dialogovém okně vyberte se třemi tečkami (![ASP.NET – Návrhář mobilních řešení elipsy](../sharepoint/media/mwellipsis.gif "ASP.NET – Návrhář mobilních řešení elipsy")) vedle položky  **Zdrojová cesta**.  
  
9. Vybrat sestavení z řešení služby SharePoint, kterou jste vytvořili v kroku 1 a potom vyberte **otevřete** tlačítko.  
  
10. V tomto příkladu ponechte **cíl nasazení** možnost jako GlobalAssemblyCache.  
  
     Tento krok způsobí, že sestavení pro nasazení do systému globální mezipaměti sestavení (GAC). Pokud chcete sestavení pro nasazení do webové aplikace (Bin) složky, vyberte tuto možnost. Další informace najdete v tématu [nasazení webové části v SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. V **bezpečné ovládací prvky** , vyberte **kliknutím sem přidejte novou položku** tlačítko.  
  
12. Zadejte hodnoty pro vlastnosti v následující tabulce.  
  
    |Název vlastnosti|Hodnota|  
    |-------------------|-----------|  
    |Obor názvů|Obor názvů plně kvalifikovaný pro kontrolu, jako například **BdcModelProject1.VisualWebPart1**.|  
    |Název typu|Button1|  
    |Název sestavení|Silné sestavení název, jako například: Microsoft.Office.SharePoint.ClientExtensions, verze = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Bezpečné|Vymazat **bezpečné** zaškrtávací políčko.|  
    |Bezpečné proti skriptu|Ponechte **skriptu bezpečné proti** zaškrtnutí políčka zrušte.|  
  
    > [!NOTE]  
    >  **Název sestavení** hodnotu pro sestavení přidány prostřednictvím **Upřesnit** kartě **návrháře balíčků** nemůže být token, musí být sestavení se silným názvem. Další informace najdete v tématu [vytvoření a použití sestavení](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Vyberte **kartě** klíč k vytvoření další položka bezpečné řízení.  
  
14. Vyberte **kliknutím sem přidejte novou položku** tlačítko znovu.  
  
15. Zadejte hodnoty pro vlastnosti v následující tabulce.  
  
    |Název vlastnosti|Hodnota|  
    |-------------------|-----------|  
    |Obor názvů|Obor názvů plně kvalifikovaný pro kontrolu, jako například **BdcModelProject1.VisualWebPart1**.|  
    |Název typu|TextBox1|  
    |Název sestavení|Silné sestavení název, jako například: Microsoft.Office.SharePoint.ClientExtensions, verze = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Bezpečné|Vyberte **bezpečné** zaškrtávací políčko.|  
    |Bezpečné proti skriptu|Vyberte **skriptu bezpečné proti** zaškrtávací políčko.|  
  
16. Vyberte **kartě** klíče a potom vyberte **OK** tlačítko dialogové okno zavřete.  
  
## <a name="see-also"></a>Viz také:
 [Zadejte informace o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Balíček a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
