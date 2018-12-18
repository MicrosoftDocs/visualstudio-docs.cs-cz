---
title: Scénáře instalace balíčku VSPackage | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c194588de8dfa8746bb79a8d86bff005d90e7550
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495931"
---
# <a name="vspackage-setup-scenarios"></a>Scénáře instalace balíčku VSPackage

Je důležité při návrhu balíčku VSPackage instalační program pro flexibilitu. Například možná budete muset v budoucnu vydání opravy zabezpečení, nebo můžete změnit strategii, která vyžaduje podpora důkladné verzí vedle sebe.

V [podporuje více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), si můžete přečíst o, jaké výhody a problémy podpory – souběžnými instalacemi sady [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s sdílené nebo vedle sebe instalací vašeho balíčku VSPackage. Stručně řečeno, rozšíření VSPackages vedle sebe získáte největší flexibilitu pro podporu nových funkcí služby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

Scénáře popsané v tomto tématu nejsou vaší jedinou možností, ale jsou uvedeny jako doporučené osvědčené postupy.

## <a name="components-privacy-and-sharing"></a>Komponenty, ochrany osobních údajů a sdílení

### <a name="make-your-components-independent"></a>Aby vaše komponenty nezávislý

Po identifikaci a naplnit součásti, přiřadit `GUID`a nasadíte komponentu, nebudete moct změnit jeho složení. Pokud změníte složení komponenty výsledné komponenty musí být nové komponenty s novou `GUID`. Zadaný tyto skutečnosti, je tím, že každá komponenta nezávislá, běžných jednotka poskytnuté nejvyšší flexibilitu správy verzí. Další informace o pravidlech, kterými se řídí součásti najdete v tématu [Změna kódu komponent](/windows/desktop/Msi/changing-the-component-code) a [co se stane, když je součástí pravidla jsou rozdělená?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Nekombinujte sdílené a privátní zdroje v součásti

Počítání odkazů probíhá na úrovni součásti. V důsledku toho kombinování sdílené a privátní zdroje v jedné součásti znemožňuje aktualizovat soukromým prostředkům, jako je spustitelný soubor, aniž byste museli také přepsat sdílené prostředky. V tomto scénáři vytváří problémům se zpětnou kompatibilitou a brání vytváření funkce vedle sebe.

Například hodnoty registru použije k registraci vašeho balíčku VSPackage pomocí [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] by měl být udržovány v komponentě odděleně od použitý k registraci vašeho balíčku VSPackage pomocí sady Visual Studio. Sdílené soubory nebo hodnoty registru přejděte v ještě jiné součásti.

## <a name="scenario-1-shared-vspackage"></a>Scénář 1: Sdílený VSPackage

V tomto scénáři sdílené VSPackage (jeden binární soubor, který podporuje více verzí sady Visual Studio je součástí balíčku Instalační služby systému Windows. Registrace s jednotlivými verzemi sady Visual Studio se řídí uživatelsky volitelných funkcí. To také znamená, že při zařazena do oddělené funkce, jednotlivé komponenty můžete vybrat jednotlivě pro instalaci nebo odinstalaci, umožňuje uživateli kontrolu nad integrace sady VSPackage v různých verzích [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Viz [funkce Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-features) Další informace o použití funkcí v balíčky Instalační služby systému Windows.)

![Instalační program balíčku VSPackage sdílené VS](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Jak je znázorněno na obrázku, sdílené komponenty jsou součástí Feat_Common funkci, která je vždy nainstalován. Tím, že funkce Feat_VS2002 a Feat_VS2003 viditelné, uživatelé mohou v době instalace do verzí sady Visual Studio chtějí balíčku VSPackage pro integraci. Uživatele můžete také používat režim údržby Instalační služby systému Windows k přidání nebo odebrání funkcí, které v tomto případě přidává a odebírá VSPackage registrační informace z různých verzí sady Visual Studio.

> [!NOTE]
> Sloupec zobrazení funkce nastavení na hodnotu 0 skrývá ho. Hodnota sloupec nízké úrovně, jako je například 1, zajistí, že bude vždy nainstalován. Další informace najdete v tématu [INSTALLLEVEL vlastnost](/windows/desktop/Msi/installlevel) a [tabulka funkcí](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scénář 2: Sdílet aktualizace balíčku VSPackage

V tomto scénáři je dodáván aktualizovanou verzi instalačního programu balíčku VSPackage ve scénáři 1. Pro účely diskuse tato aktualizace přidává podporu pro sadu Visual Studio, ale může také být jednodušší úroveň opravy zabezpečení nebo oprava chyby aktualizace service pack. Pravidla Instalační služby Windows pro instalaci součásti novější vyžadují, nejsou znovu zkopírovány beze změny součástí už v systému. V takovém případě systém s verze 1.0 již přepsat aktualizované součásti Comp_MyVSPackage.dll a umožněte uživatelům si vybrat, chcete-li přidat novou funkci Feat_VS2005 s jeho součásti Comp_VS2005_Reg.

> [!CAUTION]
> Vždy, když je VSPackage sdílen mezi více verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], je nezbytné, že novějšími verzemi sady VSPackage zachování zpětné kompatibility se staršími verzemi sady Visual Studio. Pokud nejde udržovat zpětnou kompatibilitu, je nutné použít vedle sebe, privátní balíčky VSPackages. Další informace najdete v tématu [podporuje více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Instalační program sdílené VS balíčku aktualizace VS](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Tento scénář představuje nový instalační program balíčku VSPackage využití výhod podpory Windows instalačního programu pro dílčí upgrady. Uživatelé jednoduše nainstalovat verze 1.1 a upgradu verze 1.0. Není však nutné mít verzi 1.0 v systému. Stejný instalační program nainstaluje verze 1.1 v systému bez verze 1.0. Výhodou zadejte menší upgrady tímto způsobem je, že není nutné kvůli tomu provádět práci vývoj upgrade instalačního programu a instalační program, který plně produktu. Jeden instalační program nemá obě úlohy. Opravy zabezpečení nebo service pack může místo toho využijte výhod oprav Instalační služby systému Windows. Další informace najdete v tématu [opravy a upgrady](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scénář 3: VSPackage vedle sebe

Tento scénář nabízí dva instalační programy VSPackage – jeden pro každou verzi sady Visual Studio .NET 2003 a Visual Studio. Každý instalační program nainstaluje vedle sebe nebo privátní, balíčku VSPackage (ten, který je speciálně vytvořené a nainstalovaných pro konkrétní verzi sady Visual Studio). Každý balíček VSPackage správy kódu je ve vlastní komponenty. V důsledku toho každá lze jednotlivě udržovat s opravami nebo údržby uvolní. Vzhledem k tomu, že knihovna DLL balíčku VSPackage je nyní specifické pro verzi, je bezpečné registrační informace patří pod stejnou komponentou jako knihovnu DLL.

![Instalační program balíčku VS vedle sebe VS](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Každý instalační služba také zahrnuje kód, který je sdílen mezi dva instalační programy. Pokud instalaci sdílený kód do společného umístění instalace oba soubory .msi nainstaluje sdílený kód pouze jednou. Druhý instalační program právě zvýší počet odkazů na komponentu. Počet odkazů se zajistí, že pokud jeden z rozšíření VSPackages se odinstaluje, sdílený kód zůstane pro sady VSPackage. Po odinstalaci je také druhá VSPackage, sdílený kód se odeberou.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scénář 4: Aktualizace balíčku VSPackage vedle sebe

V tomto scénáři vaše VSPackage pro sadu Visual Studio utrpělo z ohrožení zabezpečení a budete muset aktualizaci. Jako ve scénáři 2 můžete vytvořit nový soubor MSI, který aktualizuje existující instalace zahrnovat opravy zabezpečení, jakož i nasadit nové instalace s opravou zabezpečení již v místě.

V tomto případě je sady VSPackage spravované VSPackage nainstalované v globální mezipaměti sestavení (GAC). Když znovu vytvoříte tak, aby obsahovala opravy zabezpečení, je nutné změnit revize číselnou část čísla verze sestavení. Informace o registraci nové číslo verze sestavení přepíše předchozí verze, což způsobí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načíst oprava sestavení.

![Instalační program vedle sebe VS balíčku aktualizace VS](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Další informace o nasazení sestavení vedle sebe, naleznete v tématu [zjednodušuje nasazení a řešení knihovny DLL a tím zlepšují s rozhraním .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Viz také

[Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-portal)  
[Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)