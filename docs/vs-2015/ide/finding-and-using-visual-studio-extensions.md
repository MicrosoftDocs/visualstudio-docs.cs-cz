---
title: Hledání a používání rozšíření | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: df6219a66b0f6c85e197b209741706abc7ce3d06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655881"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Hledání a používání rozšíření Visual Studia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšíření sady Visual Studio jsou balíčky kódu, které se spouštějí v rámci sady Visual Studio a poskytují nové nebo vylepšené funkce sady Visual Studio. Další informace o rozšířeních sady Visual Studio najdete tady: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Můžete použít dialogové okno **rozšíření a aktualizace** k instalaci rozšíření a ukázek sady Visual Studio z webů a dalších umístění a pak je povolit, zakázat, aktualizovat nebo odinstalovat. (**Nástroje/rozšíření a aktualizace**nebo **rozšíření** typu v okně **Snadné spuštění** ). V dialogovém okně se zobrazují také aktualizace nainstalovaných ukázek a rozšíření. Můžete si také stáhnout rozšíření z webů nebo je získat od jiných vývojářů.

> [!NOTE]
> Počínaje verzí Visual Studio 2015 se rozšíření hostovaná v galerii sady Visual Studio automaticky aktualizují.  Toto nastavení můžete změnit v dialogovém okně **rozšíření a aktualizace** .  Podrobnosti najdete v části o **automatických aktualizacích rozšíření** níže.

## <a name="finding-visual-studio-extensions"></a>Hledání rozšíření sady Visual Studio
 Rozšíření můžete nainstalovat z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo [Galerie ukázek](https://code.msdn.microsoft.com/vstudio) na webu společnosti Microsoft. Rozšíření mohou být ovládací prvky, ukázky, šablony, nástroje nebo jiné součásti, které přidávají funkcionalitu do aplikace Visual Studio. Sada Visual Studio podporuje rozšíření ve formátu balíčku VSIX – patří mezi ně šablony projektů, šablony položek, položky **panelu nástrojů** , komponenty rozhraní Managed Extension Framework (MEF) a VSPackage. Můžete také stáhnout a nainstalovat rozšíření založená na MSI, ale dialogové okno **rozšíření a aktualizace** je nemůže povolit ani zakázat. Galerie sady Visual Studio obsahuje rozšíření VSIX i MSI.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Instalace nebo odinstalace rozšíření sady Visual Studio
 V části **rozšíření a aktualizace**Najděte rozšíření, které chcete nainstalovat. (Pokud znáte název nebo část názvu rozšíření, můžete hledat v okně **Hledat galerii sady Visual Studio** .) Klikněte na **Stáhnout**a pak na **instalovat**. Aby bylo možné načíst rozšíření, je nutné restartovat aplikaci Visual Studio.

 Pokud se pokusíte nainstalovat rozšíření, která obsahuje závislosti, instalační služba zkontroluje, zda jsou již tyto závislosti nainstalovány. Pokud nejsou nainstalované, dialogové okno **rozšíření a aktualizace** zobrazí seznam závislostí, které je třeba nainstalovat, než bude možné nainstalovat rozšíření.

 Pokud chcete přestat používat rozšíření, lze jej zakázat nebo odinstalovat. Zakázáním rozšíření zůstane rozšíření nainstalováno, ale nedojde k jeho načtení. Můžete zakázat pouze rozšíření VSIX; rozšíření, která byla nainstalována pomocí MSI, lze odinstalovat pouze. Najděte rozšíření a klikněte na **odinstalovat** nebo **Zakázat**. Chcete-li uvolnit zakázané rozšíření, je nutné restartovat aplikaci Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Rozšíření pro jednotlivé uživatele a administrativní rozšíření
 Většina rozšíření je pro jednotlivé uživatele a je nainstalovaná ve složce **%LocalAppData%\Microsoft\VisualStudio \\<Visual Studio verze \> \Extensions \\ ** . Některá rozšíření jsou rozšíření pro správu a jsou nainstalována do složky ** \<Visual Studio installation folder> \Common7\IDE\Extensions \\ ** .

 Chcete-li chránit systém proti rozšířením, která mohou obsahovat chyby nebo škodlivý kód, můžete omezit rozšíření vázaná na uživatele pro načtení pouze v případě, že je aplikace Visual Studio spuštěna s normálním uživatelským oprávněním. To znamená, že při spuštění sady Visual Studio s oprávněními správce jsou rozšíření vázaná na uživatele zakázána. Provedete to tak, že přejdete na stránku možnosti **rozšíření a aktualizace** (**Nástroje/možnosti**, **prostředí**, **rozšíření a aktualizace**nebo pouze **rozšíření** typu v okně **Snadné spuštění** ). Zrušte zaškrtnutí políčka **načíst rozšíření pro jednotlivé uživatele při spuštění jako správce** a pak restartujte aplikaci Visual Studio.

## <a name="automatic-extension-updates"></a>Automatické aktualizace rozšíření
 Rozšíření vázaná na uživatele se automaticky aktualizují, pokud je v galerii sady Visual Studio k dispozici nová verze.  Nová verze rozšíření se zjistí a nainstaluje na pozadí a při příštím restartování sady Visual Studio se spustí nová verze rozšíření.

 Automaticky lze aktualizovat pouze rozšíření vázaná na uživatele.  Rozšíření pro správu, která jsou nainstalována pro všechny uživatele, nebudou aktualizována a stále budete moci ručně instalovat nové verze prostřednictvím uzlu **aktualizace** **a aktualizace** dialogových oken rozšíření. Můžete zobrazit, která rozšíření budou automaticky aktualizována v podokně podrobností rozšíření v dialogovém okně **rozšíření a aktualizace** .

 Pokud chcete zakázat automatické aktualizace, můžete zakázat funkci pro všechna rozšíření nebo pouze specifická rozšíření.

- Chcete-li zakázat automatické aktualizace pro všechna rozšíření, klikněte na odkaz **změnit nastavení rozšíření a aktualizace** v dialogovém okně **rozšíření a aktualizace** a zrušte zaškrtnuté políčko **automaticky aktualizovat rozšíření**.

- Chcete-li zakázat automatické aktualizace konkrétního rozšíření, zrušte v podokně podrobností rozšíření na pravé straně dialogového okna **rozšíření a aktualizace** možnost **automaticky aktualizovat tuto příponu** .

> [!NOTE]
> Počínaje verzí Visual Studio 2015 Update 2 můžete určit (v části **Nástroje/možnosti/prostředí/rozšíření a aktualizace**), jestli chcete automatické aktualizace pro jednotlivá uživatelská rozšíření, všechna uživatelská rozšíření nebo obojí (výchozí nastavení).

## <a name="sample-master-copies-and-working-copies"></a>Ukázkové hlavní kopie a pracovní kopie
 Při instalaci online ukázky je řešení uloženo na dvou místech:

- Pracovní kopie je uložena v umístění, které jste zadali v dialogovém okně **Nový projekt** .

- Samostatná hlavní kopie je uložena v počítači.

  K provedení těchto úloh souvisejících s ukázkami můžete použít dialogové okno **rozšíření a aktualizace** :

- Zobrazit seznam hlavních kopií ukázek, které jste nainstalovali.

- Zakázat nebo odinstalovat hlavní kopii ukázky.

- Instalovat balíky ukázek, což jsou kolekce ukázek, které se týkají technologie nebo funkce.

- Nainstalujte jednotlivé online ukázky. (Můžete to provést také v dialogovém okně **Nový projekt** .)

- Zobrazit upozornění na aktualizace při zveřejnění změny zdrojového kódu nainstalovaných ukázek.

- Aktualizuje hlavní kopii nainstalované ukázky, když dojde k oznámení aktualizace.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalace bez použití rozšíření a dialogového okna Aktualizace
 Rozšíření, která byla zabalena v souboru .vsix, mohou být k dispozici v jiném umístění než v Galerii aplikace Visual Studio. Dialogové okno **rozšíření a aktualizace** nedokáže rozpoznat tyto soubory, ale můžete nainstalovat soubor. vsix dvojitým kliknutím na soubor nebo výběrem souboru a stisknutím klávesy ENTER. Pak stačí postupovat podle pokynů. Po instalaci rozšíření můžete použít dialogové okno **rozšíření a aktualizace** k jeho povolení, jeho zakázání nebo odinstalaci.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Typy rozšíření nejsou v dialogovém okně rozšíření a aktualizace podporovány.
 Visual Studio nadále podporuje rozšíření, která jsou nainstalována pomocí Instalační služby Microsoft (MSI), ale ne prostřednictvím dialogového okna **rozšíření a aktualizace** beze změn.

> [!TIP]
> Pokud rozšíření založené na MSI obsahuje soubor Extension. vsixmanifest, rozšíření se zobrazí v dialogovém okně **rozšíření a aktualizace** .
