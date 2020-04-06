---
title: Scénáře instalace balíčku VSPackage | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703976"
---
# <a name="vspackage-setup-scenarios"></a>Scénáře instalace balíčku VSPackage

Je důležité navrhnout instalační program VSPackage pro flexibilitu. V budoucnu může být například nutné uvolnit opravu zabezpečení nebo můžete změnit obchodní strategii, která vyžaduje důkladnou podporu správy verzí vedle sebe.

V [podpoře více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), můžete si přečíst o výhodách a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] problémech podpory souběžných instalací s sdílené nebo vedle sebe instalace vašeho VSPackage. Stručně řečeno, side-by-side VSPackages vám největší flexibilitu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pro podporu nových funkcí .

Scénáře popsané v tomto tématu nejsou pouze vaše možnosti, ale jsou prezentovány jako doporučené postupy.

## <a name="components-privacy-and-sharing"></a>Komponenty, ochrana osobních údajů a sdílení

### <a name="make-your-components-independent"></a>Zastavte své komponenty nezávisle

Jakmile identifikujete a naplníte `GUID`součást, přiřadíte a nasadíte komponentu, nemůžete změnit její složení. Pokud změníte složení komponenty, výsledná komponenta musí být nová `GUID`komponenta s novou . Vzhledem k těmto skutečnostem je největší flexibilita verzí poskytována tím, že každá komponenta je nezávislá, soběstačná jednotka. Další informace o pravidlech, kterými se řídí součásti, naleznete [v tématu Změna kódu komponenty](/windows/desktop/Msi/changing-the-component-code) a [Co se stane, pokud jsou pravidla komponenty porušena?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Nemíchat sdílené a soukromé prostředky v součásti

Počítání odkazů probíhá na úrovni komponenty. V důsledku toho míchání sdílených a soukromých prostředků v jedné součásti znemožňuje aktualizaci soukromých prostředků, jako je například spustitelný soubor, bez přepsání sdílených prostředků. Tento scénář vytváří problémy se zpětnou kompatibilitou a omezuje vytváření funkcí vedle sebe.

Například hodnoty registru používané k registraci [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] vašeho VSPackage s by měly být uchovávány v součásti oddělené od jedné, která slouží k registraci vašeho VSPackage s Visual Studio. Sdílené soubory nebo hodnoty registru jsou v další součásti.

## <a name="scenario-1-shared-vspackage"></a>Scénář 1: Sdílené VSPackage

V tomto scénáři sdílené VSPackage (jeden binární soubor, který podporuje více verzí sady Visual Studio je dodáván v balíčku Instalační služba systému Windows. Registrace s každou verzí sady Visual Studio je řízena funkcemi volitelnými pro uživatele. To také znamená, že při přiřazení k samostatné funkce, každá součást může být vybrána jednotlivě pro instalaci nebo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]odinstalaci, uvedení uživatele v řízení integrace VSPackage do různých verzí . (Další informace o používání funkcí v balíčcích Instalační služby systému Windows naleznete v tématu [Funkce Instalační](/windows/desktop/Msi/windows-installer-features) služby systému Windows.)

![Instalační program VS Shared VSPackage](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Jak je znázorněno na obrázku, sdílené součásti jsou součástí Feat_Common funkce, která je vždy nainstalována. Tím, že Feat_VS2002 a Feat_VS2003 funkce viditelné, uživatelé si mohou vybrat v době instalace do verze sady Visual Studio, které chtějí VSPackage integrovat. Uživatelé mohou také použít režim údržby Instalační služby systému Windows k přidání nebo odebrání funkcí, které v tomto případě přidá nebo odebere registrační informace VSPackage z různých verzí sady Visual Studio.

> [!NOTE]
> Nastavením sloupce Zobrazení funkce na 0 jej skryjete. Nízká úroveň sloupcové hodnoty, například 1, zajišťuje, že bude vždy nainstalován. Další informace naleznete v [tématu INSTALLLEVEL Property](/windows/desktop/Msi/installlevel) and [Feature Table](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scénář 2: Sdílená aktualizace vbalíčku VSPackage

V tomto scénáři je dodávána aktualizovaná verze instalačního programu VSPackage ve scénáři 1. Z důvodu diskuse aktualizace přidá podporu pro sadu Visual Studio, ale může se také jednat o jednodušší opravu zabezpečení nebo aktualizaci Service Pack pro opravu chyb. Pravidla Instalační služby systému Windows pro instalaci novějších součástí vyžadují, aby se nezměněné součásti, které jsou již v systému, nekopírovaly. V takovém případě systém s již kdispozici verze 1.0 přepíše aktualizovanou komponentu Comp_MyVSPackage.dll a umožní uživatelům přidat novou funkci Feat_VS2005 s její součástí Comp_VS2005_Reg.

> [!CAUTION]
> Vždy, když VSPackage je sdílena mezi více verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], je nezbytné, aby následné verze VSPackage udržovat zpětnou kompatibilitu s předchozími verzemi sady Visual Studio. Kde nelze zachovat zpětnou kompatibilitu, je nutné použít vedle sebe soukromé VSPackages. Další informace naleznete [v tématu Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Instalační program aktualizace sdílených balíčků VS VS](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Tento scénář představuje nový instalační program VSPackage, který využívá podporu Instalační služby systému Windows pro menší inovace. Uživatelé jednoduše nainstalovat verzi 1.1 a upgraduje verzi 1.0. Není však nutné mít v systému verzi 1.0. Stejný instalační program nainstaluje verzi 1.1 do systému bez verze 1.0. Výhodou pro poskytování menších upgradů tímto způsobem je, že není nutné projít prací na vývoji instalačního programu upgradu a instalačního programu s úplným produktem. Jeden instalační program provádí obě úlohy. Oprava zabezpečení nebo aktualizace Service Pack mohou místo toho využívat opravy Instalační služby systému Windows. Další informace naleznete v [tématu Oprava a inovace](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scénář 3: Souběžně s ním vspackage

Tento scénář představuje dva instalační programy VSPackage – jeden pro každou verzi sady Visual Studio .NET 2003 a Visual Studio. Každý instalační program nainstaluje souběžný nebo soukromý VSPackage (ten, který je speciálně sestaven a nainstalován pro konkrétní verzi sady Visual Studio). Každý VSPackage je ve své vlastní součásti. V důsledku toho může být každý jednotlivě servisován s opravami nebo uvolněním údržby. Vzhledem k tomu, že dll VSPackage je nyní specifické pro verzi, je bezpečné zahrnout jeho registrační informace ve stejné součásti jako DLL.

![Instalační program v balíčku VS Vedle strany](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Každý instalační program také obsahuje kód, který je sdílen mezi dvěma instalačními programy. Pokud je sdílený kód nainstalován do společného umístění, instalace obou souborů MSI nainstaluje sdílený kód pouze jednou. Druhý instalátor pouze instaluje počet odkazů na součásti. Počet odkazů zajišťuje, že pokud jeden z VSPackages je odinstalován, sdílený kód zůstane pro ostatní VSPackage. Pokud druhý VSPackage je také odinstalován, sdílený kód bude odebrán.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scénář 4: Aktualizace balíčku VSPackage vedle sebe

V tomto scénáři vaše VSPackage pro Visual Studio trpí chybou zabezpečení a je třeba vydat aktualizaci. Stejně jako ve scénáři 2 můžete vytvořit nový soubor MSI, který aktualizuje existující instalaci tak, aby zahrnovala opravu zabezpečení, a také nasadit nové instalace s již zavedenou opravou zabezpečení.

V tomto případě VSPackage je spravované VSPackage nainstalován v globální mezipaměti sestavení (GAC). Když ji znovu vytvoříte tak, aby zahrnovala opravu zabezpečení, je nutné změnit část čísla revize čísla verze sestavení. Informace o registraci novéverze sestavení přepíší předchozí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verzi, což způsobí načtení pevného sestavení.

![Instalační program aktualizace balíčku VS vedle sebe](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Další informace o nasazení souběžných sestavení naleznete v tématu [Zjednodušení nasazení a řešení dll peklo s rozhraním .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Viz také

- [Instalační služba systému Windows](/windows/desktop/Msi/windows-installer-portal)
- [Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
