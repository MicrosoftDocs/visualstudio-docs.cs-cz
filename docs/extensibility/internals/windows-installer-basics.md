---
title: Základy Instalační služby systému Windows | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703421"
---
# <a name="windows-installer-basics"></a>Základní informace o Instalační službě systému Windows
Instalační služba systému Windows instaluje a odinstaluje aplikace nebo softwarové produkty v počítači uživatele a provádí tyto úlohy v jednotkách nazývaných součásti Instalační služby systému Windows (někdy nazývané wic nebo pouze součásti). Identifikátor GUID identifikuje každý wic, což je základní jednotka instalace a počítání odkazů pro nastavení pomocí Instalační služby systému Windows.

 Komplexní dokumentaci K Instalační službě systému Windows naleznete v tématu sada Platform SDK, [Instalační služba systému Windows](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Vytváření balíčku VSPackage
 Instalační služba systému Windows používá instalační balíčky, které obsahují informace, které instalační program systému Windows potřebuje k instalaci, odinstalaci nebo opravě produktu a ke spuštění uživatelského rozhraní instalačního rozhraní. Každý instalační balíček obsahuje soubor MSI, který obsahuje instalační databázi, souhrnný informační tok a datové toky pro různé části instalace. Chcete-li nainstalovat instalační program, musíte vytvořit instalaci. Vzhledem k tomu, že instalační program organizuje instalace kolem konceptu součástí a ukládá informace o instalaci do relační databáze, proces vytváření instalačního balíčku obecně zahrnuje následující kroky:

1. Naplánujte si vytváření nastavení tak, aby podporovalo vaše strategie správy verzí a souběžné snímání.

2. Identifikujte funkce, které mají být prezentovány uživatelům.

3. Uspořádejte VSPackage a závislosti do komponent.

4. Naplňte instalační databázi informacemi.

5. Ověřte instalační balíček.

   Tato dokumentace se týká především prvního a třetího stupně procesu. Během těchto kroků uspořádáte funkce VSPackage do wic, abyste mohli vytvořit rámec strategie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]správy verzí a údržby tak, aby odpovídala následujícím verzím aplikace . Zbývající tři kroky jsou podrobně popsány v dokumentaci Instalační služby systému Windows v sada SDK platformy.

## <a name="key-terms"></a>Klíčové podmínky
 Následují definice klíčových pojmů souvisejících s technologií Instalační služby systému Windows.

 Soubory prostředků, klíče registru, zástupce nebo tak dále, které mohou být nainstalovány do počítače. Tyto prostředky jsou logicky seskupeny do součástí Instalační služby systému Windows.

 Součást Instalační služby systému Windows (WIC) Základní jednotka instalace představující logické seskupení souvisejících prostředků, které jsou nainstalovány a odinstalovány jako jednotka. Součásti Instalační služby systému Windows jsou označeny jedinečným ID součásti nebo identifikátorem GUID. Instalační služba systému Windows dále udržuje své referenční inventury na úrovni WIC. Pro maximální flexibilitu správy verzí nezahrnte více než jeden primární prostředek, například dll, v daném wic. Všimněte si, že po identifikaci a naplnění WIC, mu identifikátor GUID a nasadit jej, nelze změnit jeho složení. Další informace naleznete [v tématu Uspořádání aplikací do součástí](/windows/desktop/Msi/organizing-applications-into-components).

 Balíček (redist package) Jednotka nasazení, která se skládá ze souboru MSI a externích zdrojových souborů, na které by tento soubor mohl směřovat. Balíček obsahuje všechny informace, které Instalační služba systému Windows potřebuje ke spuštění hlavního nastavení a k instalaci nebo odinstalaci aplikace.

 Soubor MSI Soubor com-strukturovaný soubor úložiště obsahující pokyny a data potřebná k instalaci aplikace. Každý balíček obsahuje alespoň jeden soubor MSI. Soubor MSI obsahuje databázi instalačního programu, souhrnný informační proud a případně jednu nebo více transformací a interní zdrojové soubory. Soubory, které mají být nainstalovány, mohou být buď komprimovány do skříně a uloženy v datovém proudu v souboru MSI nebo uloženy, komprimovány nebo nekomprimovány mimo soubor MSI na zdrojovém médiu. Další informace naleznete v tématu [Windows Installer File Extensions](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Vynucení pravidel Instalační služby systému Windows
 Nasazení prostředků prostřednictvím součástí instalace určují dvě sady pravidel. Jedna sada pravidel je udržována samotnou Instalační službou systému Windows, zatímco druhou sadu byste měli vynutit jako autora instalace.

> [!NOTE]
> K vynucení pravidel Instalační služby systému Windows dochází pouze v případě, že spustíte ověření souboru MSI. Přesto budete upozorněni, abyste tato pravidla považovali za osvědčené postupy. Další informace naleznete [v tématu Ověření instalační databáze](/windows/desktop/Msi/validating-an-installation-database) a ověření [balíčku](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Pravidla vynucená instalačním programem

- Všechny soubory v dané součásti musí být nainstalovány do stejného adresáře. Naopak soubory nainstalované do samostatných složek musí patřit do samostatných součástí.

- Pro jednu komponentu může existovat pouze jedna cesta klíče. Cesta klíče je jednoduše soubor nebo klíč registru, který představuje celou součást.

#### <a name="component-provider-responsibilities"></a>Povinnosti zprostředkovatele komponent

- Všechny dva prostředky, které by mohly být dodávány samostatně v následujících verzích, by měly existovat v samostatných součástech. Prostředky by měly být seskupeny do stejné součásti pouze v případě, že jste si jisti, že tyto prostředky nebudou nikdy dodávány samostatně. Ve skutečnosti se doporučuje, aby všechny primární prostředky (například Knihovny DLL) vždy existovaly v samostatných wic. Další informace naleznete [v tématu Definování instalačních součástí](/windows/desktop/Msi/defining-installer-components).

- Žádný prostředek s verzí by nikdy neměl být dodáván ve více než jednom wic.

## <a name="see-also"></a>Viz také
- [Co se stane, pokud jsou pravidla komponenty porušena?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
