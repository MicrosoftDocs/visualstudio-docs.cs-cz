---
title: 'Řešení potíží: Návody vydání nové verze stávajícího rozšíření?'
description: Průvodce aktualizací stávajících rozšíření prostřednictvím pracovního postupu publikování.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488461"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Řešení potíží: Návody vydání nové verze stávajícího rozšíření?

> [!IMPORTANT]
> V současné době není vytváření nových rozšíření v aplikaci Visual Studio 2019 for Mac oficiálně podporováno.

Server úložiště rozšíření Visual Studio pro Mac bude přesunut 15. ledna 2021. Tento přesun nebude mít vliv na uživatele, kteří již stáhli vaše rozšíření, ale změní způsob, jakým publikujete nové verze rozšíření po tomto datu.

Jako autor existující přípony budete muset při vydání dalších aktualizací použít jiný pracovní postup. Tento proces se skládá z těchto součástí:
- Nastavuje se veřejné úložiště GitHub pro každé rozšíření.
- Sdílení adresy URL úložiště s Visual Studio pro Mac týmu prostřednictvím [seznamu adresátů pro publikování v rozšíření](mailto:vsmextpub@microsoft.com)
- Aktualizace rozšíření pomocí funkce releases v GitHubu


## <a name="initial-setup"></a>Počáteční nastavení 

Aby bylo možné pokračovat v publikování aktualizací vašich rozšíření, budete muset vytvořit veřejné úložiště GitHub. Pokud publikujete více rozšíření, budete muset mít samostatné úložiště pro každou z nich, pokud je nebudete vždy používat a publikujete společně. v takovém případě můžete použít jedno úložiště.

> [!NOTE]
> I když úložiště GitHub pro vaše rozšíření musí být veřejné, nemusíte hostovat žádný z vašich kódů. Po tomto procesu není nutné mít žádný kód v GitHubu.


## <a name="share-the-location-of-your-repository"></a>Sdílení umístění úložiště

Jakmile nastavíte úložiště, odešlete e-mailovou zprávu na [seznam adresátů pro publikování](mailto:vsmextpub@microsoft.com) s adresou URL.


## <a name="release-a-new-version"></a>Vydání nové verze

K zahájení procesu aktualizace rozšíření použijete odkaz vytvořit nové vydání na hlavní stránce úložiště. Po výběru tohoto odkazu postupujte následovně:

1. Přidat informace do **verze značky verze** v následujícím formátu

    > v \<releaseVersion> \- VSM\<targetVersion>

    Kde:
     - **&lt; releaseVersion &gt;** je číslo verze rozšíření.
     - **&lt; targetVersion &gt;** je minimální verze Visual Studio pro Mac vaše rozšíření cílí na

2. Volitelné Pole **název** a **Popis** mohou být vyplněna libovolnými informacemi, které byste chtěli chtít; Tento pracovní postup nepoužívá informace v těchto polích.

3. Ujistěte se, že políčko předběžná **verze** není zaškrtnuté. Pokud je zaškrtnuto, nebude tento proces publikování vyzvednut vydání.

4. Připojte soubory **. MPack** , které implementují vaše rozšíření v sekci **binárních souborů** . V této verzi je možné připojit více souborů **. MPack** .

Visual Studio pro Mac zobrazí nejnovější verzi rozšíření, která je kompatibilní s instalací Visual Studio pro Mac, která byla použita pro přístup k úložišti rozšíření.

Pokud jste své úložiště GitHub zaregistrovali Visual Studio pro Mac týmem, vaše verze rozšíření se během 24 hodin vybere Visual Studio pro Mac.

## <a name="additional-information"></a>Další informace

- Verze, které neodpovídají výše uvedeným požadavkům, nebudou publikovány. 
- Od 15. ledna 2021 se aktualizace rozšíření zobrazí jenom v Visual Studio pro Mac 8,0 nebo novějším.
- Stávající rozšíření zůstanou k dispozici pro Visual Studio pro Mac uživatelů bez jakékoli akce na vaší straně. Pokud publikujete novou verzi po 15. lednu 2021, stačí postupovat podle pokynů v této příručce.
