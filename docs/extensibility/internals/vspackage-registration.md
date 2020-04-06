---
title: Registrace vbalíčku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703924"
---
# <a name="vspackage-registration"></a>Registrace balíčku VSPackage
VSPackages musí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poradit, že jsou nainstalovány a měly by být načteny. Tento proces se provádí zápisem informací do registru. To je typická práce instalátoru.

> [!NOTE]
> Je přijata praxe během vývoje VSPackage použít vlastní registraci. Partneři [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] však nemohou odesílat své produkty pomocí vlastní registrace jako součást nastavení.

 Položky registru v balíčku Instalační služby systému Windows jsou obvykle uvedeny v tabulce Registru. Můžete také zaregistrovat přípony souborů v tabulce Registru. Instalační služba systému Windows však poskytuje integrovanou podporu prostřednictvím programového identifikátoru (ProgId), třídy, rozšíření a tabulky sloves. Další informace naleznete v [tématu Databázové tabulky](/windows/desktop/Msi/database-tables).

 Ujistěte se, že položky registru jsou přidruženy k součásti, která je vhodná pro vybranou strategii vedle sebe. Položky registru pro sdílený soubor by měly být například přidruženy k součásti Instalační služby systému Windows tohoto souboru. Podobně položky registru pro soubor specifický pro verzi by měly být přidruženy k součásti tohoto souboru. V opačném případě instalace nebo odinstalace vspackage pro jednu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verzi může přerušit váš VSPackage v jiných verzích. Další informace naleznete [v tématu Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Nejjednodušší způsob, jak spravovat registraci, je použít stejná data ve stejných souborech jak pro registraci vývojáře, tak pro registraci v době instalace. Například některé instalační vývojové nástroje mohou využívat soubor ve formátu .reg v době sestavení. Pokud vývojáři udržují soubory REG pro svůj každodenní vývoj a ladění, mohou být tyto stejné soubory automaticky zahrnuty do instalačního programu. Pokud nemůžete automaticky sdílet registrační údaje, musíte zajistit, aby kopie registračních dat instalačním programem byla aktuální.

## <a name="registering-unmanaged-vspackages"></a>Registrace nespravovaných balíčků VSPackages
 Nespravované balíčky VSPackages (včetně těch, které jsou generovány šablonou balíčku sady Visual Studio) používají k ukládání registračních informací soubory RGS ve stylu knihovny ATL. Formát souboru RGS je specifický pro atl a obecně nemůže být spotřebován jako-je pomocí instalačního vývojového nástroje. Informace o registraci instalačního programu VSPackage musí být udržovány samostatně. Vývojáři mohou například uchovávat soubory ve formátu REG synchronizované se změnami souborů RGS. Soubory REG mohou být sloučeny s RegEdit pro vývojové práce nebo spotřebovány instalačním programem.

## <a name="registering-managed-vspackages"></a>Registrace spravovaných balíčků VSPackages
 Nástroj RegPkg čte atributy registrace ze spravovaného balíčku VSPackage a může buď zapisovat informace přímo do registru, nebo zapisovat soubory formátu REG, které mohou být spotřebovány instalačním programem.

> [!NOTE]
> Nástroj RegPkg není redistribuovatelný a nelze jej použít k registraci balíčku VSPackage v systému uživatele.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Proč By VSPackages by neměla self-Register v době instalace
 Instalátory VSPackage by neměly spoléhat na vlastní registraci. Na první pohled udržování hodnoty registru VSPackage pouze v VSPackage sám se zdá jako dobrý nápad. Vzhledem k tomu, že vývojáři potřebují hodnoty registru, které jsou k dispozici pro jejich rutinní práci a testování, má smysl vyhnout se udržování samostatné kopie dat registru v instalačním programu. Instalační program se může spolehnout na samotného balíčku VSPackage při zápisu hodnot registru.

 Zatímco dobré v teorii, self-registrace má několik chyb, které dělají to nevhodné pro instalaci VSPackage:

- Správná podpora instalace, odinstalace, vrácení instalace a vrácení zpět od instalace vyžaduje, abyste vytvořili čtyři vlastní akce pro každý spravovaný balíček VSPackage, který se sám registruje voláním RegPkg.

- Váš přístup k souběžné podpoře může vyžadovat, abyste vytvořili čtyři vlastní akce, které vyvolávají RegSvr32 nebo RegPkg pro každou podporovanou verzi aplikace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Instalaci s moduly registrovanými samostatně nelze bezpečně vrátit zpět, protože neexistuje žádný způsob, jak říct, zda jsou vlastní registrované klíče používány jinou funkcí nebo aplikací.

- Samoobslkované knihovny DLL někdy odkazují na pomocné knihovny DLL, které nejsou k dispozici nebo jsou nesprávnou verzí. Naproti tomu Instalační služba systému Windows může zaregistrovat knihovny DLL pomocí tabulek registru bez závislosti na aktuálním stavu systému.

- Vlastní registrační kód může být odepřen přístup k síťovým prostředkům, jako jsou knihovny typů, pokud je komponenta zadána jako run-from-source a je uvedena v tabulce SelfReg. To může způsobit selhání instalace součásti během instalace pro správu.

## <a name="see-also"></a>Viz také
- [Instalační služba systému Windows](/windows/desktop/Msi/windows-installer-portal)
- [Registrace spravovaného balíčku](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
