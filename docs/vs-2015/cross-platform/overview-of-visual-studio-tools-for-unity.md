---
title: Přehled Visual Studio Tools for Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: ba5447301c3a5581d35825ed91c17b3c9f50015f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298750"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Přehled Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této části se dozvíte víc o funkcích Visual Studio Tools for Unity nabídek a o tom, jak je můžete využít k zajištění vyšší produktivity pomocí Unity.  
  
 Pomocí Visual Studio Tools for Unity (*VSTU*) můžete použít Visual Studio k psaní herních a editorových skriptů v jazyce C# a pak pomocí výkonného ladicího programu vyhledat a opravit chyby. Nejnovější vydaná verze VSTU zahrnuje barvy syntaxe pro jazyk shaderu ShaderLab Unity, lepší vizualizace ladicího programu a vylepšené generování kódu pro Průvodce MonoBehavior. VSTU také přináší vaše soubory projektu Unity, zprávy konzoly a možnost začít hru do sady Visual Studio, abyste mohli při psaní kódu strávit méně času přepínání do a z editoru Unity.  
  
 Další informace o těchto funkcích najdete v tématu o tom, jak dál číst.  
  
## <a name="integration-with-unity"></a>Integrace s Unity  
 Pokud jste museli kdykoliv přepínat mezi editorem Unity a Visual Studiem, Visual Studio Tools for Unity by nedošlo k vylepšení produktivity. To je důvod, proč Visual Studio Tools for Unity usnadňuje práci bez chodu sady Visual Studio.  
  
- **Průzkumník projektů Unity** zobrazí celý projekt Unity v rámci sady Visual Studio pomocí stejné hierarchie zobrazené v editoru Unity.  
  
- Integrace konzoly Unity zobrazuje výstup z konzoly Unity přímo v okně chyb sady Visual Studio.  
  
- Zahájit ladění hry ze sady Visual Studio – není nutné přepínat zpátky na Unity, stačí stisknout klávesu F5.  
  
## <a name="superior-debugging"></a>Vynikající ladění  
 Připojte výkonný ladicí program sady Visual Studio k vaší hře Unity pro ladění skriptů a knihoven DLL v jazyce C# bez ohledu na to, jestli běží samostatně nebo v editoru Unity. Můžete použít všechny funkce ladění, které očekáváte od sady Visual Studio.  
  
- Zarážky, včetně podmíněných zarážek.  
  
- Vyhodnotit složité výrazy v okno Kukátko.  
  
- Zkontrolujte a upravte hodnotu proměnných a argumentů.  
  
- Přechod k podrobnostem o komplexních objektech a datových strukturách.  
  
  Můžete dokonce ladit hru Unity, když běží na jiném počítači v síti.  
  
## <a name="productivity"></a>Produktivita  
 Kromě zavedené produktivity sady Visual Studio pro psaní a refaktoring kódu v jazyce C# Visual Studio Tools for Unity poskytuje další funkce produktivity pro vývojáře Unity.  
  
- Zvýrazňování syntaxe pro ShaderLab jazyk Unity vám pomůže odhalit chyby v shaderech předtím, než se stanou chybami. Stačí otevřít soubory ShaderLab v aplikaci Visual Studio.  
  
- Průvodce MonoBehavior vám umožňuje procházet seznam chování Unity a vytvářet často používaný kód pro chování, která nemusíte znát. Stiskněte kombinaci kláves CTRL + SHIFT + M.  
  
- Jakmile se seznámíte s chováním Unity, které používáte nejčastěji, Průvodce rychlým MonoBehaviorm je napravuje na dosah ruky. Stiskněte kombinaci kláves CTRL + ALT + Q.  
  
- Přístup k dokumentaci Unity ze sady Visual Studio. Stačí zvýraznit volání rozhraní API, o které chcete získat informace, a pak stisknout kombinaci kláves CTRL + ALT + M, CTRL + H.  
  
- Pomocí klávesových zkratek získáte přístup ke všem funkcím a dalším.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Visual Studio Tools for Unity API  
 Přizpůsobení a rozšíření chování Visual Studio Tools for Unity pomocí poskytnutých rozhraní API.  
  
- Visual Studio Tools for Unity zaregistruje zpětné volání protokolu, aby bylo možné vytvořit streamování konzoly Unity do sady Visual Studio. Pokud máte skripty editoru, které protokolují informace, můžete je připojit ke stejnému zpětnému volání, abyste mohli odesílat zprávy do sady Visual Studio. Další informace najdete v příkladu zpětného volání protokolu.  
  
- Způsob, jakým Visual Studio Tools for Unity generuje soubory projektu, můžete změnit pomocí zpětného volání stylu Unity ProjectFileGeneration. Další informace naleznete v příkladu generování souboru projektu.  
  
## <a name="see-also"></a>Viz také  
 [Domovská stránka Unity](https://unity.com/)
