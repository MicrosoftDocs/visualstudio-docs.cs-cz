---
title: Hledání a používání rozšíření | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8de9a0394c72043bc54dd6fa0632d3ed3e6edfd5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062797"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Hledání a používání rozšíření Visual Studia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšíření sady Visual Studio jsou balíčky kódu, které v prostředí Visual Studio a které poskytují nové nebo vylepšené funkce aplikace Visual Studio. Můžete najít další informace o rozšíření sady Visual Studio tady: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Můžete použít **rozšíření a aktualizace** dialogové okno instalace rozšíření sady Visual Studio a ukázky z webů a dalších míst a pak povolit, zakázat, aktualizovat nebo je odinstalovat. (**Nástrojů / rozšíření a aktualizace**, nebo typ **rozšíření** v **Snadné spuštění** okno). Dialogové okno zobrazuje také aktualizace nainstalovaných ukázek a rozšíření. Můžete také stáhnout rozšíření z webů nebo získat od jiných vývojářů.

> [!NOTE]
>  Spouští se v sadě Visual Studio 2015, rozšíření hostované ve Galerii Visual Studio se automaticky aktualizují.  Toto nastavení můžete změnit **rozšíření a aktualizace** dialogového okna.  Naleznete v části **automatické aktualizace rozšíření** níže podrobnosti.

## <a name="finding-visual-studio-extensions"></a>Vyhledání rozšíření sady Visual Studio
 Můžete nainstalovat rozšíření z [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=178891) nebo [Galerie ukázek](http://go.microsoft.com/fwlink/?LinkId=245175) na webu společnosti Microsoft. Rozšíření mohou být ovládací prvky, ukázky, šablony, nástroje nebo jiné součásti, které přidávají funkcionalitu do aplikace Visual Studio. Visual Studio podporuje rozšíření ve formátu balíčku VSIX – to zahrnuje šablony projektu, šablony položek, položky **nástrojů** položky, komponenty spravovaných rozšíření Framework (MEF) a rozšíření VSPackages. Můžete také stáhnout a nainstalovat rozšíření založená na Instalační služby MSI, ale **rozšíření a aktualizace** dialogové okno nelze povolit ani zakázat. Galerie Visual Studio obsahuje rozšíření VSIX a instalační služby MSI.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Instalace nebo odinstalace rozšíření sady Visual Studio
 V **rozšíření a aktualizace**, najít rozšíření, které chcete nainstalovat. (Pokud znáte název nebo část názvu rozšíření, je možné hledat **Prohledat Galerii Visual Studio** okna.) Klikněte na tlačítko **Stáhnout**, pak **nainstalovat**. Aby bylo možné načíst rozšíření je nutné restartovat Visual Studio.

 Pokud se pokusíte nainstalovat rozšíření, která obsahuje závislosti, instalační služba zkontroluje, zda jsou již tyto závislosti nainstalovány. Pokud tyto produkty nejsou nainstalovány, **rozšíření a aktualizace** dialogové okno obsahuje závislosti, které je třeba nainstalovat před instalací rozšíření.

 Pokud chcete přestat používat rozšíření, lze jej zakázat nebo odinstalovat. Zakázáním rozšíření zůstane rozšíření nainstalováno, ale nedojde k jeho načtení. Můžete zakázat pouze rozšíření VSIX; rozšíření, které jsou nainstalované s použitím Instalační služba MSI lze pouze odinstalovat. Najít rozšíření a klikněte na tlačítko **odinstalovat** nebo **zakázat**. Aby bylo možné uvolnění zakázaného rozšíření je nutné restartovat Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Rozšíření pro jednotlivé uživatele a administrativní rozšíření
 Většina rozšíření jsou rozšíření vázaná na uživatele a jsou nainstalovaná v **%LocalAppData%\Microsoft\VisualStudio\\< verze sady Visual Studio\>\Extensions\\**  složky. Několik rozšíření jsou administrativní rozšíření a jsou nainstalovaná v **\<instalační složky sady Visual Studio > \Common7\IDE\Extensions\\** složky.

 Pro ochranu systému proti rozšíření, které mohou obsahovat chyby nebo škodlivý kód, můžete omezit rozšíření vázaná na uživatele pro načtení pouze při spuštění sady Visual Studio s oprávněními běžných uživatelů. To znamená, že je zakázáno rozšíření vázaná na uživatele, při spuštění sady Visual Studio s oprávněními správce. Chcete-li to provést, přejděte na **rozšíření a aktualizace** stránka možností (**Nástroje / možnosti**, **prostředí**, **rozšíření a aktualizace**, nebo jen typ **rozšíření** v **Snadné spuštění** okno). Zrušte **načítání rozšíření pro jednotlivé uživatele při spuštění jako správce** zaškrtněte políčko a potom restartujte Visual Studio.

## <a name="automatic-extension-updates"></a>Aktualizace automatické rozšíření
 Rozšíření vázaná na uživatele se automaticky aktualizují při ve Galerii Visual Studio je dostupná nová verze.  Nová verze rozšíření rozpoznán a nainstalován na pozadí a při příštím restartování sady Visual Studio, používat novou verzi rozšíření.

 Jen rozšíření vázaná na uživatele je možné automaticky aktualizovat.  Administrativní rozšíření, která jsou nainstalována pro všechny uživatele, neaktualizuje se a ručně nainstalujte nové verze prostřednictvím **rozšíření a aktualizace** dialogové okno **aktualizace** uzlu. Uvidíte, jaká rozšíření se automaticky aktualizují v podokně podrobností rozšíření **rozšíření a aktualizace** dialogového okna.

 Pokud chcete zakázat automatické aktualizace, můžete zakázat funkci pro všechny přípony nebo pouze konkrétní rozšíření.

-   Chcete-li zakázat automatické aktualizace pro všechna rozšíření, klikněte na tlačítko **změnit nastavení rozšíření a aktualizace** odkaz na **rozšíření a aktualizace** dialogové okno a zrušte zaškrtnutí políčka **automaticky aktualizovat rozšíření**.

-   Chcete-li zakázat automatické aktualizace pro konkrétní příponu, zrušte zaškrtnutí políčka **automaticky aktualizovat toto rozšíření** možnost v podokně podrobností rozšíření na pravé straně **rozšíření a aktualizace** dialogového okna.

> [!NOTE]
>  Od verze Visual Studio 2015 Update 2, můžete zadat (v **Nástroje / možnosti / prostředí / rozšíření a aktualizace**) určuje, zda chcete automatické aktualizace pro rozšíření vázaná na uživatele, všechna rozšíření uživatele nebo obě (výchozí nastavení).

## <a name="sample-master-copies-and-working-copies"></a>Ukázka hlavní kopie a pracovní kopie
 Při instalaci online ukázky je řešení uloženo na dvou místech:

- Pracovní kopie je uložena v umístění, které jste zadali v **nový projekt** dialogové okno.

- Samostatná hlavní kopie je uložena v počítači.

  Můžete použít **rozšíření a aktualizace** dialogové okno k provedení těchto úloh týkajících se ukázek:

- Zobrazit seznam hlavních kopií ukázek, které jste nainstalovali.

- Zakázat nebo odinstalovat hlavní kopii ukázky.

- Instalovat balíky ukázek, což jsou kolekce ukázek, které se týkají technologie nebo funkce.

- Nainstalujte jednotlivé online ukázky. (Můžete to provést také v **nový projekt** dialogové okno.)

- Zobrazit upozornění na aktualizace při zveřejnění změny zdrojového kódu nainstalovaných ukázek.

- Aktualizujte hlavní kopii nainstalované ukázky, když je oznámení o aktualizaci.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalace bez použití rozšíření a dialogového okna Aktualizace
 Rozšíření, která byla zabalena v souboru .vsix, mohou být k dispozici v jiném umístění než v Galerii aplikace Visual Studio. **Rozšíření a aktualizace** dialogové okno nelze rozpoznat tyto soubory, ale můžete nainstalovat soubor .vsix poklepáním na soubor, nebo výběrem souboru a stisknutím klávesy ENTER. Potom postupujte podle pokynů. Pokud je rozšíření nainstalované, můžete použít **rozšíření a aktualizace** dialogové okno povolit, zakázat nebo ho odinstalujte.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Typy rozšíření nepodporuje rozšíření a aktualizace dialogové okno
 Visual Studio i nadále podporuje rozšíření, které instaluje Microsoft Installer (MSI) ale není až **rozšíření a aktualizace** dialogové okno bez úprav.

> [!TIP]
>  Pokud rozšíření využívajícím MSI obsahuje soubor extension.vsixmanifest, rozšíření se zobrazí v **rozšíření a aktualizace** dialogové okno.
