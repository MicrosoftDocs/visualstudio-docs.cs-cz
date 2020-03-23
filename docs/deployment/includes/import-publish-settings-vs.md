---
ms.openlocfilehash: 8adac174fbc78778e7154a205088fb9e9a57ae4a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143520"
---

1. V počítači, ve kterém je v aplikaci Visual Studio otevřen a ASP.NET projektu, klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení a zvolte **Publikovat**.

1. Pokud jste dříve nakonfigurovali profily publikování, zobrazí se podokno **Publikovat.** Klepněte na **tlačítko Vytvořit nový profil**.

1. V **dialogovém** okně Vybrat cíl publikování klikněte na **Importovat profil**.

    ![Zvolte Publikovat](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Přejděte do umístění souboru nastavení publikování, který jste vytvořili v předchozí části.

1. V dialogovém okně **Importovat soubor nastavení publikování** přejděte na profil vytvořený v předchozí části a vyberte jej a klepněte na **tlačítko Otevřít**.

    Visual Studio zahájí proces nasazení a okno Výstup zobrazuje průběh a výsledky.

    Pokud se zobrazí chyby nasazení, klikněte na **Nastavení** a upravte nastavení. Upravte nastavení a kliknutím na **Ověřit otestujte** nová nastavení. Pokud název hostitele nebyl nalezen, zkuste adresu IP namísto názvu hostitele v polích Adresa URL **serveru** a **cíle.**

    ![Úpravy nastavení v nástroji Publikovat](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
