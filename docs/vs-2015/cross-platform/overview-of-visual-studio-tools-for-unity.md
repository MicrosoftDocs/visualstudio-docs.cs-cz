---
title: Přehled nástrojů visual studia pro jednotu | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: ba5447301c3a5581d35825ed91c17b3c9f50015f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74298750"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Přehled Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této části se dozvíte další informace o funkcích Visual Studio Nástroje pro unity nabízí a jak je můžete použít, aby se stala produktivnější s Unity.  
  
 Pomocí visual studio nástroje pro jednotu (*VSTU*), můžete použít Visual Studio psát skripty hry a editor v jazyce C# a pak použít jeho výkonný ladicí program najít a opravit chyby. Nejnovější verze VSTU obsahuje syntaxi zbarvení pro Unity shaderLab shader jazyk, lepší ladicí vizuály a vylepšené generování kódu pro průvodce MonoBehavior. VSTU také přináší soubory projektu Unity, konzolové zprávy a možnost spustit hru do sady Visual Studio, takže můžete strávit méně času přepínáním do a z Unity Editor při psaní kódu.  
  
 Pokračujte ve čtení, abyste se dozvěděli více o těchto funkcích.  
  
## <a name="integration-with-unity"></a>Integrace s unity  
 Visual Studio Tools for Unity by nebylo zvýšení produktivity, pokud jste museli přepínat tam a zpět mezi editorunity a Visual Studio po celou dobu. To je důvod, proč Visual Studio Tools for Unity usnadňuje pokračovat v práci bez opuštění sady Visual Studio.  
  
- **Unity Project Explorer** zobrazí celý projekt Unity uvnitř Visual Studia pomocí stejné hierarchie zobrazené v editoru Unity.  
  
- Integrace konzoly Unity zobrazuje výstup z konzoly Unity přímo v okně chyb visual studio.  
  
- Začněte ladit svou hru z Visual Studia – není třeba přepnout zpět na Unity, stačí stisknout Klávesu F5.  
  
## <a name="superior-debugging"></a>Vynikající ladění  
 Připojte výkonný ladicí program sady Visual Studio k vaší hře Unity a laděte skripty jazyka C# a knihovny DLL bez ohledu na to, zda je spuštěn samostatně nebo v editoru Unity. Můžete použít všechny funkce ladění, které očekáváte od sady Visual Studio.  
  
- Zarážky, včetně podmíněných zarážek.  
  
- Vyhodnoťte složité výrazy v okně Kukátka.  
  
- Zkontrolujte a upravte hodnotu proměnných a argumentů.  
  
- Přechod k podrobnostem o složitých objektech a datových strukturách.  
  
  Můžete dokonce ladit hru Unity, zatímco běží na jiném počítači v síti.  
  
## <a name="productivity"></a>Produktivita  
 Kromě produktivity visual studio je zavedená pro psaní a refaktoring kódu v jazyce C#, Visual Studio Tools for Unity poskytuje další funkce produktivity pro vývojáře Unity.  
  
- Syntaxe zbarvení pro jazyk Unity ShaderLab vám pomůže rozpoznat chyby ve vašich shaders dříve, než se stanou chyby. Stačí otevřít soubory ShaderLab v sadě Visual Studio.  
  
- Průvodce MonoBehavior umožňuje procházet seznam unity chování a vytvoří často používaný kód pro chování, které nemusí být obeznámeni s. Stiskněte kombinaci kláves CTRL+SHIFT+M.  
  
- Jakmile se seznámíte s chováním Unity, které používáte nejčastěji, průvodce Rychlé monochování je umístí přímo na dosah ruky. Stiskněte kombinaci kláves CTRL+ALT+Q.  
  
- Přístup unity dokumentace z Visual Studia. Stačí zvýraznit volání rozhraní API, o kterém se chcete dozvědět, a stiskněte kombinaci kláves CTRL+ALT+M, CTRL+H.  
  
- Přístup ke všem těmto funkcím a dalším funkcím pomocí klávesových zkratek.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Nástroje Visual Studio pro rozhraní Unity API  
 Přizpůsobte a rozšiřte chování nástrojů sady Visual Studio pro jednotu pomocí zadaných api.  
  
- Visual Studio Tools for Unity zaregistruje zpětné volání protokolu, aby mohl streamovat konzolu Unity do sady Visual Studio. Pokud máte skripty editoru, které protokolují informace, můžete je připojit do stejné zpětné volání a odesílat zprávy do sady Visual Studio. Další informace naleznete v příkladu zpětného volání protokolu.  
  
- Můžete změnit způsob, jakým Nástroje sady Visual Studio pro jednotu generuje soubory projektu pomocí zpětného volání stylu Unity ProjectFileGeneration. Další informace naleznete v příkladu generování souboru projektu.  
  
## <a name="see-also"></a>Viz také  
 [Domovská stránka Unity](https://unity.com/)
