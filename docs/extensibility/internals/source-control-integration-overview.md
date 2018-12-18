---
title: Přehled integrace správy zdrojového | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: edd2e04f4e1102d66cc04cd1365dc7abd1488c9c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931834"
---
# <a name="source-control-integration-overview"></a>Přehled integrace správy zdrojového kódu
Tato část porovná dva způsoby, jak integrovat do správy zdrojového kódu sady Visual Studio; ovládací prvek zdroje modulu Plug-in a VSPackage, která poskytuje source řešení pro řízení a označuje nové funkce správy zdrojového kódu. Visual Studio umožňuje ruční přepínání mezi balíčků VSPackage správy zdrojového kódu a ovládací prvek moduly plug-in zdrojového kódu, stejně jako automatické přepínání založené na řešení.  
  
## <a name="source-control-integration"></a>Integrace správy zdrojového kódu  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podporuje dva typy možností integrace správy zdrojového kódu. Ve všech verzích [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], stále můžete integrovat modulu plug-in podle rozhraní zdroje ovládacího prvku modulu Plug-in API (dříve také označuje jako rozhraní API MSSCCI), které poskytuje funkce správy základní zdrojového kódu při používání sady Visual Studio zdrojového ovládacího prvku uživatelského rozhraní ( UŽIVATELSKÉ ROZHRANÍ). VSPackage správy zdrojového kódu na druhé straně poskytuje novou, hloubkové integrace [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] cesty, které jsou vhodné pro integraci správy zdrojového kódu, která vyžaduje vysokou úroveň vyspělosti a autonomie v jeho model správy zdrojového kódu.  
  
 ![Přehled ovládacího prvku zdroje](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Modul Plug-in správy zdrojového kódu  
 Všechny verze sady Visual Studio podporují rozhraní API modulu Plug-in zdroje ovládacího prvku specifikace verze 1.2 jako cestu k integraci. Zdrojový ovládací prvek modulu plug-in implementátora zapíše knihovnu DLL, která implementuje rozhraní API modulu Plug-in zdroje ovládacího prvku funkce integrace správy zdrojového kódu a registrace, jak je popsáno v [vytváření modulu Plug-in zdrojového ovládacího prvku](../../extensibility/internals/creating-a-source-control-plug-in.md). V takovém případě integrované vývojové prostředí (IDE) používá [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelského rozhraní pro dialogová okna, jako je vrácení se změnami, rezervace, stránky vlastností nástroje/Možnosti, panely nástrojů a glyfy zdrojového ovládacího prvku. Striktní dodržování rozhraní API modulu Plug-in zdroje ovládacího prvku zajistí snadnou integraci do sady Visual Studio a o bezproblémové prostředí pro uživatele. To znamená, že modul plug-in správy zdrojového kódu musí implementovat většinu funkcí a zpětná volání, které jsou podrobně popsané v rozhraní API.  
  
 K implementaci modulu plug-in pomocí rozhraní API pro zdrojový ovládací prvek modulu Plug-in správy zdrojového kódu, postupujte podle těchto kroků:  
  
1. Vytvořit knihovnu DLL, která implementuje funkcí zadaných v [moduly plug-in správy zdrojových kódů](../../extensibility/source-control-plug-ins.md).  
  
2. Zaregistruje knihovnu DLL tak, že položky odpovídající registru (popsané v [postupy: Instalace modulu Plug-in zdrojového ovládacího prvku](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3. Vytvořte pomocné rutiny uživatelského rozhraní a zobrazení po zobrazení výzvy zdrojový ovládací prvek adaptér balíček (součást sady Visual Studio, která zajišťuje funkce správy zdrojového kódu pomocí ovládacího prvku moduly plug-in zdrojového kódu)  
  
   V reakci na příkaz řízení zdroje integrovaném vývojovém prostředí sady Visual Studio nabízí standardní uživatelské rozhraní pro základní operace a potom předává informace do správy zdrojového kódu modulu plug-in prostřednictvím funkce definované v rozhraní API modulu Plug-in zdroje ovládacího prvku. Pro pokročilé možnosti modulu plug-in správy zdrojového kódu může být volána na prezentovat své vlastní uživatelské rozhraní, například procházení projektu se spravovanými zdroji. To znamená, že uživatel může se vám dva by mohly mít odlišné styly uživatelského rozhraní při práci se správou zdrojového kódu: rozhraní, které nabízí Visual Studio a rozhraní, které představuje modul plug-in správy zdrojového kódu. Toto je nejvíce patrné s operací správy zdrojů pokročilé.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Nevýhody prováděcí modul Plug-in správy zdrojového kódu  
  
-   Pro pokročilé funkce může uživatel zobrazit dva různé styly rozhraní, což vede k potenciální záměna.  
  
-   Modul plug-in správy zdrojového kódu je omezena na model správy zdrojového kódu odvozené od rozhraní API modulu Plug-in zdroje ovládacího prvku.  
  
-   Rozhraní API modulu Plug-in zdroje ovládacího prvku může být příliš omezující pro některých scénářích správy zdrojového kódu.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Výhody pro implementaci modulu Plug-in správy zdrojového kódu  
  
-   Visual Studio poskytuje uživatelské rozhraní pro všechny operace základní zdroj ovládacího prvku tak, aby modul plug-in správy zdrojového kódu není nutné implementovat potenciálně velmi složitý uživatelského rozhraní.  
  
-   Z důvodu striktní rozhraní API modul plug-in správy zdrojového kódu můžete snadno komunikovali s programy ovládací prvek externího zdroje nakonfigurovánu rozsáhlejší; Visual Studio nezáleží, příliš daleko, jak funkce správy zdrojového se provádí, pouze to, že se provádí podle rozhraní API modulu Plug-in zdroje ovládacího prvku.  
  
-   Je snazší implementovat než balíčku VSPackage správy zdrojového kódu modulu plug-in správy zdrojového kódu.  
  
## <a name="source-control-vspackage"></a>Ovládací prvek zdroje balíčku VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Umožňuje těsnou integraci s Visual Studio s úplnou kontrolu nad funkce správy zdrojového kódu a úplné nahrazení zadaného sady Visual Studio zdrojového ovládacího prvku uživatelského rozhraní. Ovládací prvek zdroje balíčku VSPackage zaregistrován pomocí sady Visual Studio a poskytuje funkce správy zdrojového kódu. I když pomocí sady Visual Studio lze registrovat několika správy zdrojového kódu rozšíření VSPackages, pouze jeden z nich může být aktivní v daný okamžik. Balíčku VSPackage správy zdrojového kódu má plnou kontrolu nad funkce správy zdrojového kódu a vzhled v sadě Visual Studio, zatímco je aktivní. Všechny ostatní správy zdrojového kódu rozšíření VSPackages, které mohou být registrovány v systému nejsou aktivní a vůbec nezobrazí žádné uživatelské rozhraní.  
  
 Implementace balíčku VSPackage správy zdrojového kódu vyžaduje strategii "všechno nebo nic". Tvůrce balíčku VSPackage správy zdrojového kódu musí investovat značné úsilí při implementaci řady rozhraní ovládacího prvku zdroje a nových prvků uživatelského rozhraní (dialogová okna, nabídek a panelů nástrojů) se věnuje funkcím celý zdrojový ovládací prvek. Zobrazit [vytváření VSPackage ovládací prvek zdroje](../../extensibility/internals/creating-a-source-control-vspackage.md) další podrobnosti.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Nevýhody implementace VSPackage zdrojového ovládacího prvku  
  
-   Počet složitých rozhraní pro integraci s Visual Studio úspěšně musí implementovat sady VSPackage.  
  
-   Sady VSPackage musíte zadat všechna rozhraní požadované pro správu zdrojového kódu; Visual Studio bude poskytovat bez pomoci v této oblasti.  
  
-   Ovládací prvek zdroje balíčku VSPackage úzce souvisí se sadou Visual Studio a nelze použít samostatné programy, takže funkce nelze snadno sdílet s externí verzi zdrojového ovládacího prvku programu.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Výhody implementace VSPackage zdrojového ovládacího prvku  
  
-   Protože sady VSPackage má plnou kontrolu nad správy zdrojového kódu uživatelského rozhraní a funkce, uživateli zobrazí s bezproblémové rozhraní pro správu zdrojového kódu.  
  
-   Sady VSPackage nejsou omezené na konkrétní zdrojového ovládacího prvku modelu.  
  
## <a name="see-also"></a>Viz také  
 [Správy zdrojového kódu](../../extensibility/internals/source-control.md)   
 [Vytvoření modulu Plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Vytvoření zdrojového ovládacího prvku VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Co je nového ve správě zdrojového kódu](../../extensibility/internals/what-s-new-in-source-control.md)