---
title: Základy Instalační služby systému Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73d1462cd6a5dacf57939ae06e7b490235483a60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843129"
---
# <a name="windows-installer-basics"></a>Základní informace o Instalační službě systému Windows
Instalační program Windows instaluje a odinstaluje aplikací nebo softwarové produkty na počítači uživatele, provedení těchto úloh v jednotkách nazývaných součásti Instalační služby systému Windows (říká se jim WICs nebo pouze komponenty). Identifikátor GUID identifikuje každý WIC, což je základní jednotkou instalace a pro nastavení pomocí Instalační služby systému Windows pro počítání odkazů.  
  
 Úplnou dokumentaci Instalační služby systému Windows, naleznete v tématu Platform SDK [Instalační služby systému Windows](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Vytváření VSPackage  
 Instalační služby systému Windows používá instalační balíčky, které obsahují informace, které instalační služby systému Windows potřebuje k instalaci, odinstalaci nebo oprava produktu a spusťte instalační program uživatelského rozhraní (UI). Každý instalační balíček obsahuje soubor MSI, který obsahuje instalační databáze, datového proudu souhrnné informace a datových proudů různými částmi instalace. Pokud chcete použít instalační program, je nutné vytvořit instalace. Vzhledem k tomu, že instalační program uspořádá zařízení kolem koncepce součásti a ukládá informace o instalaci v relační databázi, proces vytváření instalačního balíčku široce zahrnuje následující kroky:  
  
1. Plánování nastavení pro vytváření pro podporu správy verzí a strategie vedle sebe.  
  
2. Určete funkce, které se budou zobrazovat uživateli.  
  
3. VSPackage a závislosti uspořádejte do složek.  
  
4. Naplnění databáze instalace informace.  
  
5. Ověření instalace balíčku.  
  
   Tato dokumentace se týká především první a třetí kroků procesu. Při provádění těchto kroků můžete uspořádat vaše funkce balíčku VSPackage do WICs, můžete snímek vaší správy verzí a údržba strategie pro další verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Zbývající tři kroky jsou podrobně popsány v dokumentaci Platform SDK Instalační služby systému Windows.  
  
## <a name="key-terms"></a>Klíčové pojmy  
 Následují definice klíčových pojmů související s technologií Instalační služby systému Windows.  
  
 Prostředek  
 Soubory, klíče registru, klávesové zkratky, nebo a tak dále, který může být instalován do počítače. Tyto prostředky jsou logicky seskupeny do součásti Instalační služby systému Windows.  
  
 Součást Instalační služby systému Windows (WIC)  
 Základní jednotka instalace představující logické seskupení souvisejících prostředků, které se instaluje a odinstaluje jako celek. Instalační služby systému Windows součásti jsou označeny ID jedinečné součásti nebo identifikátor GUID. Kromě toho Instalační služby systému Windows udržuje jeho úrovni WIC pro počítání odkazů. Pro správu verzí maximální flexibilitu a zahrnout do dané WIC více než jednu primární prostředek, jako je například knihovny DLL. Všimněte si, že po identifikaci a naplnit WIC, poskytněte identifikátor GUID a nasaďte ho, nelze změnit jeho složení. Další informace najdete v tématu [uspořádání aplikace do komponenty](/windows/desktop/Msi/organizing-applications-into-components).  
  
 Balíček (Redist balíček)  
 Jednotka nasazení, které obsahuje soubor .msi a externí zdrojové soubory, ke kterým může odkazovat tento soubor. Balíček obsahuje všechny informace, které instalační služby systému Windows je potřeba ke spuštění uživatelského rozhraní a instalace nebo odinstalace aplikace.  
  
 Soubor MSI  
 Soubor modelu COM strukturované úložiště obsahující pokyny a data požadovaná k instalaci aplikace. Každý balíček obsahuje alespoň jeden soubor MSI. Tento soubor .msi obsahuje instalační databáze, datový proud souhrnné informace a může být jeden nebo více transformací a interní zdrojové soubory. Soubory k instalaci můžete buď být komprimována do souboru a uložená v datovém proudu v souboru MSI nebo uložené, komprimované nebo nekomprimovaný mimo soubor .msi na zdrojové médium. Další informace najdete v tématu [přípony souborů Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-file-extensions).  
  
## <a name="windows-installer-rules-enforcement"></a>Vynucení pravidel Instalační služby systému Windows  
 Dvě sady pravidel určit nasazení prostředků prostřednictvím součásti vašeho nastavení. Jedna sada pravidel se spravuje pomocí Instalační služby systému Windows, samostatně, zatímco druhá sada jako autor instalace by měl vynutit.  
  
> [!NOTE]
>  Vynucení pravidla Instalační služby systému Windows dojde pouze v případě, že spuštění ověření souboru .msi. Nicméně můžete se zobrazí se upozornění považovat za těchto pravidel osvědčených postupů. Další informace najdete v tématu [ověřování databáze instalace](/windows/desktop/Msi/validating-an-installation-database) a [ověřování balíčku](/windows/desktop/Msi/package-validation).  
  
#### <a name="installer-enforced-rules"></a>Pravidla vynucovat instalačního programu  
  
-   Všechny soubory v dané součásti musí být nainstalovány do stejného adresáře. Naopak soubory nainstalovat do samostatné složky musí patřit do samostatné součásti.  
  
-   Může existovat jenom jedna cesta ke klíči jednotlivé komponenty. Jako cestu ke klíči je jednoduše souborů nebo registru klíč, který představuje celé součást.  
  
#### <a name="component-provider-responsibilities"></a>Součást poskytovatele odpovědnosti  
  
-   Žádné dva prostředky, které může dodávat odděleně v budoucích verzích by měla existovat v jednotlivých součástí. Prostředky by měly být seskupeny do pod stejnou komponentou pouze v případě, že jste si jisti, že tyto prostředky se nikdy dodávat odděleně. Ve skutečnosti se doporučuje, všechny primární prostředky (například DLL) vždy v samostatných WICs existovat. Další informace najdete v tématu [definování komponenty instalačního programu](/windows/desktop/Msi/defining-installer-components).  
  
-   Ve více než jeden WIC by nikdy dodávat systémovou správou verzí se žádný prostředek.  
  
## <a name="see-also"></a>Viz také  
 [Co se stane, pokud jsou porušení pravidla komponenty?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)