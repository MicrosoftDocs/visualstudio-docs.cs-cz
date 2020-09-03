---
title: Základy Instalační služba systému Windows | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703421"
---
# <a name="windows-installer-basics"></a>Základní informace o Instalační službě systému Windows
Instalační služba systému Windows nainstaluje a odinstaluje aplikace nebo softwarové produkty v počítači uživatele. tyto úlohy se provádějí v jednotkách nazývaných Instalační služba systému Windows součásti (někdy označované jako WICs nebo pouze komponenty). Identifikátor GUID identifikuje každou součást WIC, což je základní jednotka instalace a počítání odkazů pro nastavení pomocí Instalační služba systému Windows.

 Ucelenou dokumentaci Instalační služba systému Windows naleznete v tématu sada SDK platformy [Instalační služba systému Windows](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Vytváření balíčku VSPackage
 Instalační služba systému Windows používá instalační balíčky obsahující informace, které Instalační služba systému Windows potřebuje k instalaci, odinstalaci nebo opravě produktu a ke spuštění uživatelského rozhraní instalace (UI). Každý instalační balíček obsahuje soubor. msi, který obsahuje instalační databázi, souhrnný informační Stream a datové proudy pro různé části instalace. Chcete-li použít instalační program, je nutné vytvořit instalaci. Vzhledem k tomu, že instalační program organizuje instalaci v souvislosti s konceptem komponent a ukládá informace o instalaci v relační databázi, proces vytváření instalačního balíčku bude široce zahrnovat následující kroky:

1. Naplánujte vytváření obsahu pro podporu vaší verze a souběžných strategií.

2. Identifikujte funkce, které se uživatelům zobrazí.

3. Uspořádejte VSPackage a závislosti do komponent.

4. Naplňte do instalační databáze informace.

5. Ověřte instalační balíček.

   Tato dokumentace se primárně zabývá prvním a třetím postupem procesu. Během těchto kroků uspořádáte funkce VSPackage do WICs, abyste mohli při provádění strategie správy verzí a údržby zohlednit další verze nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Zbývající tři kroky jsou podrobně popsány v dokumentaci Instalační služba systému Windows v sadě SDK platformy.

## <a name="key-terms"></a>Klíčové výrazy
 Níže jsou uvedené definice klíčových pojmů souvisejících s technologií Instalační služba systému Windows.

 Soubory prostředků, klíče registru, zástupce nebo a tak dále mohou být nainstalovány do počítače. Tyto prostředky jsou logicky seskupeny do komponent Instalační služba systému Windows.

 Instalační služba systému Windows Component (WIC) základní jednotka instalace představující logické seskupení souvisejících prostředků, které jsou nainstalované a odinstalované jako jednotka. Komponenty Instalační služba systému Windows jsou identifikovány jedinečným IDENTIFIKÁTORem součásti nebo identifikátorem GUID. Kromě toho Instalační služba systému Windows udržuje svůj odkaz počítání na úrovni WIC. Pro zajištění maximální flexibility zahrňte do dané sady WIC více než jeden primární prostředek, jako je například knihovna DLL. Všimněte si, že když identifikujete a naplníte třídu WIC, přiřadíte jí identifikátor GUID a nasadíte ji, nemůžete změnit její složení. Další informace najdete v tématu [uspořádání aplikací do komponent](/windows/desktop/Msi/organizing-applications-into-components).

 Balíček (Redist Package) jednotka nasazení, která se skládá ze souboru. msi a externích zdrojových souborů, na které může tento soubor ukazovat. Balíček obsahuje všechny informace, které Instalační služba systému Windows potřebují ke spuštění uživatelského rozhraní a k instalaci nebo odinstalaci aplikace.

 Soubor. msi soubor úložiště strukturovaný modelem COM obsahující pokyny a data potřebná k instalaci aplikace. Každý balíček obsahuje alespoň jeden soubor. msi. Soubor. MSI obsahuje databázi instalačního programu, souhrnný informační Stream a případně jednu nebo více transformací a interní zdrojové soubory. Soubory, které se mají nainstalovat, se buď komprimují do souboru CAB, a ukládají se do datového proudu v souboru. msi nebo uložené, komprimované nebo nekomprimované, mimo soubor. msi na zdrojovém médiu. Další informace najdete v tématu [Instalační služba systému Windows přípony souborů](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Vynucování pravidel Instalační služba systému Windows
 Dvě sady pravidel určují nasazení prostředků přes komponenty instalačního programu. Jedna sada pravidel je udržována Instalační služba systému Windows sám, zatímco druhou sadu je potřeba vyhovět jako autor instalace.

> [!NOTE]
> Vynucování Instalační služba systému Windows pravidel probíhá pouze v případě, že spustíte ověření souboru. msi. Je ale potřeba se s těmito pravidly zacházet jako s osvědčenými postupy. Další informace najdete v tématu [ověření instalační databáze](/windows/desktop/Msi/validating-an-installation-database) a [ověření balíčku](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Pravidla vynutilá instalačním programem

- Všechny soubory v dané součásti musí být nainstalovány do stejného adresáře. Naopak soubory nainstalované do samostatných složek musí patřit k samostatným součástem.

- Může existovat pouze jedna cesta ke klíči na komponentu. Klíčovou cestou je pouze soubor nebo klíč registru, který představuje celou komponentu.

#### <a name="component-provider-responsibilities"></a>Odpovědnosti poskytovatele součástí

- Všechny dva prostředky, které se mohou samostatně dodávat v následujících verzích, by měly existovat v samostatných součástech. Prostředky by se měly seskupovat do stejné komponenty jenom v případě, že jste si jisti, že tyto prostředky nikdy nebudou dodávat samostatně. Ve skutečnosti se doporučuje, aby všechny primární prostředky (například knihovny DLL) vždy existovaly v samostatných WICs. Další informace najdete v tématu [Definování komponent instalačního programu](/windows/desktop/Msi/defining-installer-components).

- Žádný prostředek s verzí by se nikdy neměl dodávat ve více než jedné ze součástí.

## <a name="see-also"></a>Viz také
- [Co se stane, když jsou pravidla komponent poškozená?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
