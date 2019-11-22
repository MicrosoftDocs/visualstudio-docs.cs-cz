---
title: 'Postupy: vytvoření ovládacího prvku panelu nástrojů, který používá model Windows Forms | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox control
- winforms
- toolbox
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: 8436b8eee0193715e4ae886db18f91f7148dcb3b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300427"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Postupy: vytvoření ovládacího prvku panelu nástrojů, který používá model Windows Forms
Šablona ovládacího prvku panelu nástrojů model Windows Forms, která je obsažena v [!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] umožňuje vytvořit model Windows Forms ovládací prvky, které jsou automaticky přidány do **sady nástrojů** při instalaci rozšíření. V tomto tématu se dozvíte, jak použít šablonu k vytvoření ovládacího prvku **sady nástrojů** , který můžete distribuovat dalším uživatelům.  
  
> [!NOTE]
> Chcete-li zjistit, jak stáhnout sadu Visual Studio SDK, přečtěte si téma [středisko pro vývojáře rozšiřitelnosti sady Visual Studio](https://go.microsoft.com/fwlink/?linkid=121964) na webu MSDN.  
  
## <a name="creating-a-toolbox-control"></a>Vytvoření ovládacího prvku panelu nástrojů  
 Pro vytvoření projektu použijte šablonu ovládacího prvku panelu nástrojů model Windows Forms a potom v Návrháři Sestavte uživatelské rozhraní (UI).  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>Vytvoření projektu ovládacího prvku model Windows Forms Toolbox  
  
1. V nabídce **soubor** klikněte na příkaz **Nový**a potom klikněte na **projekt**.  
  
2. V dialogovém okně **Nový projekt** v části **Nainstalované šablony**klikněte na uzel pro preferovaný programovací jazyk a pak klikněte na **rozšiřitelnost**. V seznamu typů projektů vyberte **model Windows Forms ovládací prvek panelu nástrojů**.  
  
3. Do pole **název** zadejte název, který chcete použít pro projekt. Klikněte na tlačítko **OK**.  
  
     Sada Visual Studio vytvoří řešení, které obsahuje uživatelský ovládací prvek, atribut pro vložení ovládacího prvku do **panelu nástrojů**a manifest VSIX pro nasazení.  
  
#### <a name="to-build-the-control-ui"></a>Sestavení uživatelského rozhraní ovládacího prvku  
  
1. V **Průzkumník řešení**poklikejte na ToolboxControl.cs a otevře se v návrháři.  
  
2. Z **panelu nástrojů**přetáhněte všechny ovládací prvky, které chcete na návrhovou plochu, a uspořádejte je podle svého návrhu.  
  
3. V okně **vlastnosti** nastavte veřejné vlastnosti pro uživatelský ovládací prvek a podřízené ovládací prvky.  
  
## <a name="coding-the-control"></a>Kódování ovládacího prvku  
 Ve výchozím nastavení se ovládací prvek zobrazí v **panelu nástrojů** jako **ToolboxControl1** ve skupině položek **panelu nástrojů** , která má stejný název jako vaše řešení. Tyto názvy můžete změnit v souboru ToolboxControl.cs.  
  
#### <a name="to-code-the-control"></a>Pro kód ovládacího prvku  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem na ToolboxControl.cs a potom kliknutím na **Zobrazit kód** otevřete soubor v zobrazení kódu.  
  
2. V definici částečné třídy, která implementuje ovládací prvek, klikněte pravým tlačítkem myši na název třídy, klikněte na **Refaktorovat**a pak klikněte na **Přejmenovat**. Změňte název třídy na název, který chcete zobrazit v **sadě nástrojů** při instalaci ovládacího prvku.  
  
3. Přímo nad definicí třídy v deklaraci atributu `ProvideToolboxControl` změňte hodnotu prvního parametru na název skupiny položek, která bude hostovat ovládací prvek v **sadě nástrojů**.  
  
     Následující příklad ukazuje atribut `ProvideToolboxControl` a upravenou definici třídy pro ovládací prvek s názvem `Counter` ve skupině `General` položky.  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4. Implementujte vlastnosti, metody a události pro ovládací prvek.  
  
## <a name="building-testing-and-deployment"></a>Sestavování, testování a nasazování  
 Stisknutím klávesy F5 sestavíte projekt, který obsahuje soubor nasazení. vsix, a otevře druhou instanci sady Visual Studio, která má ovládací prvek nainstalovaný v **sadě nástrojů**.  
  
#### <a name="to-build-and-test-the-control"></a>Sestavení a otestování ovládacího prvku  
  
1. Stiskněte klávesu F5.  
  
2. V nové instanci aplikace Visual Studio vytvořte projekt aplikace model Windows Forms.  
  
3. Vyhledejte ovládací prvek v **sadě nástrojů** a přetáhněte jej na návrhovou plochu.  
  
4. V okně **vlastnosti** ověřte, zda jsou vlastnosti zobrazeny podle očekávání.  
  
5. Přidejte jakýkoliv kód nebo další ovládací prvky, které jsou požadovány k otestování metod a událostí.  
  
6. Stisknutím klávesy F5 otevřete aplikaci model Windows Forms.  
  
7. Ověřte, že vlastnosti, metody a události vašeho ovládacího prvku se chovají podle očekávání.  
  
#### <a name="to-deploy-the-control"></a>Nasazení ovládacího prvku  
  
1. Po sestavení testovaného projektu otevřete složku \bin\debug\ projektu v Průzkumníku souborů a vyhledejte soubor. VSIX.  
  
2. Nahrajte soubor. vsix do sítě nebo na web.  
  
     Pokud soubor nahrajete na [Visual Studio Marketplace](https://marketplace.visualstudio.com/) web, jiní uživatelé mohou použít **Správce rozšíření** v aplikaci Visual Studio k vyhledání ovládacího prvku a jeho instalaci.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření ovládacího prvku panelu nástrojů WPF](../extensibility/creating-a-wpf-toolbox-control.md)