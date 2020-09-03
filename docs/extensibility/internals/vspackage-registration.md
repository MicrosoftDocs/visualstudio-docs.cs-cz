---
title: Registrace balíčku VSPackage | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703924"
---
# <a name="vspackage-registration"></a>Registrace balíčku VSPackage
VSPackage musí poradit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , že jsou nainstalované a měly by být načteny. Tento proces je možné provést zápisem informací do registru. To je typická úloha instalačního programu.

> [!NOTE]
> Jedná se o přijatý postup při vývoji VSPackage pro použití samoobslužné registrace. Partneři ale [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] nemůžou své produkty dodávat pomocí samoobslužné registrace jako součást instalace.

 Položky registru v balíčku Instalační služba systému Windows jsou obvykle vytvořeny v tabulce registru. Můžete také zaregistrovat přípony souborů v tabulce registru. Instalační služba systému Windows však poskytuje integrovanou podporu prostřednictvím tabulek programového identifikátoru (ProgId), třídy, rozšíření a slovesa. Další informace najdete v tématu [databázové tabulky](/windows/desktop/Msi/database-tables).

 Ujistěte se, že jsou položky registru přidruženy k součásti, která je vhodná pro vaši vybranou souběžnou strategii. Například položky registru pro sdílený soubor by měly být přidruženy k Instalační služba systému Windows komponentě tohoto souboru. Také položky registru pro soubor pro konkrétní verzi by měly být přidruženy k komponentě tohoto souboru. V opačném případě instalace nebo odinstalace sady VSPackage pro jednu verzi nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] může poškodit VSPackage v jiných verzích. Další informace najdete v tématu [Podpora více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Nejjednodušší způsob, jak spravovat registraci, je použít stejná data ve stejných souborech pro jak registraci vývojáře, tak i registraci v době instalace. Některé nástroje pro vývoj instalačního programu můžou například spotřebovávat soubor ve formátu. reg v době sestavení. Pokud vývojáři udržují soubory. reg pro vlastní každodenní vývoj a ladění, mohou být tyto soubory v instalačním programu automaticky zahrnuty. Pokud nemůžete automaticky sdílet registrační data, je nutné zajistit, aby byla kopie registračních dat instalačního programu aktuální.

## <a name="registering-unmanaged-vspackages"></a>Registrace nespravovaných VSPackage
 Nespravované sady VSPackage (včetně těch, které jsou vygenerované šablonou balíčku sady Visual Studio) používají k ukládání registračních informací soubory. rgs ve stylu ATL. Formát souboru. rgs je specifický pro knihovnu ATL a nelze ho obecně spotřebovat pomocí nástroje pro tvorbu instalace. Registrační informace pro instalační program VSPackage se musí uchovávat samostatně. Vývojáři mohou například uchovávat soubory ve formátu REG v synchronizaci se změnami souborů. rgs. Soubory. reg lze sloučit s regedit pro vývoj práce nebo spotřebované instalačním programem.

## <a name="registering-managed-vspackages"></a>Registrace spravovaných VSPackage
 Nástroj RegPkg čte registrační atributy ze spravovaného VSPackage a může buď zapisovat informace přímo do registru, nebo zapisovat soubory. reg, které může instalační program spotřebovat.

> [!NOTE]
> Nástroj RegPkg není Distribuovatelný a nedá se použít k registraci VSPackage v systému uživatele.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Proč by VSPackage neměly být samy registrovat v době instalace
 Instalátory VSPackage by se neměli spoléhat na vlastní registraci. Na první pohled, pokud chcete, aby hodnoty registru VSPackage pouze v balíčku VSPackage vypadaly jako dobrý nápad. Vzhledem k tomu, že vývojáři potřebují k dispozici hodnoty registru pro svou běžnou práci a testování, má smysl, aby se zabránilo zachování samostatné kopie dat registru v instalačním programu. Instalační program může pro zápis hodnot registru spoléhat sám na VSPackage.

 I když je v koúrovni teoretická, má Automatická registrace několik vad, které ji nehodí pro instalaci VSPackage:

- Správná podpora instalace, odinstalace, vrácení se změnami instalace a vrácení odinstalace vyžaduje, abyste vytvořili čtyři vlastní akce pro každý spravovaný VSPackage, který registruje sami voláním RegPkg.

- Váš přístup k souběžné podpoře může vyžadovat, abyste vytvořili čtyři vlastní akce, které vyvolávají RegSvr32 nebo RegPkg pro každou podporovanou verzi nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Instalaci se samotnými registrovanými moduly nejde bezpečně vrátit zpátky, protože neexistuje žádný způsob, jak sdělit, jestli jsou klíče registrované místně používané jinou funkcí nebo aplikací.

- Samostatně registrované knihovny DLL někdy odkazují na pomocné knihovny DLL, které nejsou k dispozici, nebo se jedná o nesprávnou verzi. Naproti tomu Instalační služba systému Windows může registrovat knihovny DLL pomocí tabulek registru bez závislosti na aktuálním stavu systému.

- Kód pro samostatnou registraci je možné odepřít přístup k síťovým prostředkům, jako jsou knihovny typů, pokud je komponenta zadána jako spustit ze zdroje a je uvedena v tabulce SelfReg. To může způsobit selhání instalace komponenty při instalaci pro správu.

## <a name="see-also"></a>Viz také
- [Instalační služba systému Windows](/windows/desktop/Msi/windows-installer-portal)
- [Registrace spravovaného balíčku](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
