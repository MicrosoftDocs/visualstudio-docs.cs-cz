---
title: Registrace balíčku VSPackage | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67b80eb48129fb989822e28bcb0ac0e330c426bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828421"
---
# <a name="vspackage-registration"></a>Registrace balíčku VSPackage
Rozšíření VSPackages musíte poradit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , že jsou nainstalované a měli byste jej načíst. Tento proces se provádí pomocí zápisu informací do registru. To je typické úlohy instalačního programu.  
  
> [!NOTE]
>  Přijaté praxe je během vývoje VSPackage používat samoobslužné registrace. Ale [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partneři nelze odeslat vlastních produktů s využitím samoregistračního jako součást instalace.  
  
 Položky registru do balíčku Instalační služby systému Windows jsou obecně provedené v tabulce registru. Přípony souborů budete taky moct registrovat v tabulce registru. Ale instalační služby systému Windows obsahuje integrovanou podporu prostřednictvím programový identifikátor (ProgId), třída, rozšíření a operaci tabulky. Další informace najdete v tématu [databázových tabulek](/windows/desktop/Msi/database-tables).  
  
 Ujistěte se, že vaše položky registru jsou spojeny s komponenta, která je vhodná pro vaši zvolenou strategii vedle sebe. Položky registru pro sdílený soubor například by měly být přidružené komponenty tento soubor Instalační služby systému Windows. Položky registru pro konkrétní verzi souboru, by měly být přidružené tento soubor komponenty. V opačném případě instalace nebo odinstalace vašeho balíčku VSPackage pro jednu verzi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] by mohlo narušit vaše VSPackage v dalších verzích. Další informace najdete v tématu [podporuje více verzí sady Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Nejjednodušší způsob, jak spravovat registraci se má používat stejná data v stejné soubory, které pro vývojáře registrace i registrace čas instalace. Některé nástroje pro vývoj instalačního programu například může spotřebovat soubor ve formátu .reg v okamžiku sestavení. Pokud vývojáři udržovat .reg soubory pro každodenní vývoj a ladění, tyto stejné soubory mohou být zahrnuty v instalačním programu automaticky. Pokud nemůžete sdílet automaticky registrační data, musíte zajistit, že je aktuální kopii instalačního programu registrační data.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrace balíčků VSPackage nespravované  
 Nespravované rozšíření VSPackages (včetně těch, které generuje šablonou balíček služby Visual Studio) knihovny ATL – vizuální styl .rgs soubory použít k ukládání informací o registraci. Formát souboru .rgs je specifická pro knihovny ATL a nejde je využívat obecně jako-je při instalaci nástroje pro vytváření. Informace o registraci pro instalační program balíčku VSPackage musí být udržovány odděleně. Například vývojáři můžou synchronizaci souborů ve formátu .reg s .rgs změny souborů. Soubor .reg můžete sloučit s RegEdit při vývojových pracích nebo používané instalační program.  
  
## <a name="registering-managed-vspackages"></a>Registrace spravovaných rozšíření VSPackages  
 Nástroj RegPkg načteme spravované VSPackage atributy registrace a buď přímo do registru nebo soubory ve formátu .reg zápisu, které mohou být spotřebovány instalační program, zapsat informace.  
  
> [!NOTE]
>  Nástroj RegPkg není distribuovatelné součásti a nelze použít k registraci balíčku VSPackage v systému uživatele.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Proč rozšíření VSPackages by měl samoobslužné nezaregistroval v době instalace  
 Vaše instalační programy VSPackage neměli byste tedy spoléhat na automatickou registraci. Na první pohled zachování hodnot registru balíčku VSPackage pouze v balíčku VSPackage samotný vypadá jako dobrý nápad. Oznámeno, že vývojáři potřebují k dispozici hodnoty registru pro své běžné práci a testování, je vhodné vyhnout zachování samostatnou kopii dat registru v instalačním programu. Instalační program můžete spolehnout na samotný balíčku VSPackage pro zápis hodnoty registru.  
  
 Při dobré teoreticky samoregistračního má několik chyby, které usnadňují nevhodný pro instalaci balíčku VSPackage:  
  
- Správně podporuje instalaci, odinstalaci, vrácení instalace zpět a vrácení odinstalace je potřeba vytvořit čtyři vlastní akce pro každý spravovaný VSPackage, která se svým registruje voláním RegPkg.  
  
- Váš přístup k podpoře vedle sebe může vyžadovat, že vytvoříte čtyři vlastní akce, které vyvolají RegSvr32 nebo RegPkg pro každou podporovanou verzi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
- Instalace s místním registrované moduly nelze bezpečně vrátit zpět, protože neexistuje žádný způsob sdělit, pokud automaticky registrována klíče se používají jiné funkce nebo aplikace.  
  
- Automaticky registrována knihovny DLL někdy propojit pomocné knihovny DLL, které nejsou k dispozici nebo jsou nesprávné verze. Naproti tomu Instalační služby systému Windows můžete zaregistrovat knihovny DLL pomocí registru tabulky nejsou závislé na aktuální stav systému.  
  
- Samoregistračního kódu může být odepřen přístup k síťovým prostředkům, jako jsou knihovny typů, pokud komponenta je zadán jako spuštění ze zdroje i je uveden v tabulce SelfReg. To může způsobovat instalace součásti selhání během instalace pro správu.  
  
## <a name="see-also"></a>Viz také  
 [Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-portal)   
 [Registrace spravovaného balíčku](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)