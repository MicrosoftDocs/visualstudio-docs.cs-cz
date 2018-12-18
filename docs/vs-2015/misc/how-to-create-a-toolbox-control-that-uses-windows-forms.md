---
title: 'Postupy: vytvoření ovládacího prvku panel nástrojů, který používá Windows Forms | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Toolbox control
- winforms
- toolbox
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 2860f3fca32b3a87967a404fb47626416d9f5dce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263715"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Postupy: vytvoření ovládacího prvku panel nástrojů, který používá Windows Forms
Šablony ovládacího prvku Windows Forms panel nástrojů, který je součástí [!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] umožňuje vytvořit ovládací prvky Windows Forms, které jsou automaticky přidány do **nástrojů** při instalaci rozšíření. Toto téma ukazuje, jak použít šablonu k vytvoření **nástrojů** ovládacího prvku, které můžete distribuovat ostatním uživatelům...  
  
> [!NOTE]
>  Stažení sady Visual Studio SDK naleznete v tématu [středisko pro vývojáře rozšiřitelnosti Visual Studio](http://go.microsoft.com/fwlink/?linkid=121964) na webové stránce MSDN.  
  
## <a name="creating-a-toolbox-control"></a>Vytvoření ovládacího prvku panel nástrojů  
 Pomocí šablony ovládacího prvku Windows Forms panel nástrojů pro vytvoření projektu a následně vytvořit uživatelské rozhraní (UI) v návrháři.  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>Vytvoření projektu ovládacího prvku Windows Forms panelu nástrojů  
  
1.  Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** dialogovém okně **nainstalované šablony**, klikněte na uzel Upřednostňovaný programovací jazyk a potom klikněte na tlačítko **rozšiřitelnost**. V seznamu typů projektů, vyberte **ovládacího prvku Windows Forms panel nástrojů**.  
  
3.  V **název** zadejte název, kterou chcete použít pro projekt. Klikněte na tlačítko **OK**.  
  
     Visual Studio vytvoří řešení, která obsahuje uživatelského ovládacího prvku, atributu vložit ovládací prvek **nástrojů**, a manifest VSIX pro nasazení.  
  
#### <a name="to-build-the-control-ui"></a>Chcete-li vytvořit ovládací prvek uživatelského rozhraní  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte na panel ToolboxControl.cs ho otevřete v návrháři.  
  
2.  Z **nástrojů**, všechny ovládací prvky, které chcete přetáhnout na návrhovou plochu a uspořádat je podle vašeho návrhu.  
  
3.  V **vlastnosti** okno, nastavte veřejné vlastnosti na uživatelský ovládací prvek a podřízené ovládací prvky.  
  
## <a name="coding-the-control"></a>Kódování ovládacího prvku  
 Ve výchozím nastavení, zobrazí se váš ovládací prvek v **nástrojů** jako **ToolboxControl1** v **nástrojů** skupiny položek, který má stejný název jako vaše řešení. Tyto názvy v souboru ToolboxControl.cs můžete změnit.  
  
#### <a name="to-code-the-control"></a>Do kódu ovládacího prvku  
  
1.  V **Průzkumníka řešení**ToolboxControl.cs pravým tlačítkem myši a potom klikněte na tlačítko **zobrazit kód** k otevření souboru v zobrazení kódu.  
  
2.  V definici dílčí třídě, která implementuje ovládací prvek, klikněte pravým tlačítkem na název třídy, klikněte na tlačítko **Refaktorovat**a potom klikněte na tlačítko **přejmenovat**. Změnit název třídy na název, který chcete zobrazit v **nástrojů** při instalaci ovládacího prvku.  
  
3.  Přímo nad definici třídy v `ProvideToolboxControl` atribut deklarace, změňte hodnotu prvního parametru na název skupiny položek, který bude hostitelem ovládacího prvku **nástrojů**.  
  
     Následující příklad ukazuje `ProvideToolboxControl` atribut a definice upravené třídy pro ovládací prvek s názvem `Counter` v `General` skupiny položek.  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4.  Implementace vlastnosti, metody a události pro ovládací prvek.  
  
## <a name="building-testing-and-deployment"></a>Sestavování, testování a nasazení  
 Stisknutím klávesy F5 projekt, který obsahuje soubor .vsix nasazení a otevře se druhé instance sady Visual Studio, který má ovládací prvek nainstalovaný v sestavení **nástrojů**.  
  
#### <a name="to-build-and-test-the-control"></a>Pro vytváření a testování ovládacího prvku  
  
1.  Stiskněte klávesu F5.  
  
2.  V nové instanci sady Visual Studio vytvořte projekt Formulářové aplikace Windows.  
  
3.  Najít ovládací prvek ve **nástrojů** a přetáhněte jej na návrhovou plochu.  
  
4.  V **vlastnosti** okna, ověřte, že vaše vlastnosti zobrazují podle očekávání.  
  
5.  Přidejte kód nebo další ovládací prvky, které jsou nutné k testovací metody a události.  
  
6.  Stisknutím klávesy F5 spusťte aplikaci Windows Forms.  
  
7.  Ověřte, že vlastnosti, metody a události ovládacího prvku se chovat dle očekávání.  
  
#### <a name="to-deploy-the-control"></a>Nasazení ovládacího prvku  
  
1.  Po sestavení testovaného projektu, otevřete složku \bin\debug\ projektu v Průzkumníku souborů a vyhledejte soubor .vsix.  
  
2.  Nahrajte soubor .vsix k síti nebo na web.  
  
     Pokud nahrajete soubor, který má [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) webové stránky, další uživatelé můžou používat **Správce rozšíření** v sadě Visual Studio najít ovládací prvek a nainstalujte ho.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření ovládacího prvku panelu nástrojů WPF](../extensibility/creating-a-wpf-toolbox-control.md)