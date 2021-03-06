---
ms.openlocfilehash: 94c2c733b631ef5e727c79a6e093bb224aec38c4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249878"
---

1. V počítači, kde máte otevřený projekt ASP.NET v aplikaci Visual Studio, klikněte pravým tlačítkem na projekt v Průzkumník řešení a vyberte **publikovat**.

   Pokud jste již dříve nakonfigurovali všechny publikační profily, otevře se podokno **publikování** . Klikněte na **Nový** nebo **vytvořte nový profil**.

1. Vyberte možnost importu profilu.

   ::: moniker range=">=vs-2019"
   V dialogovém okně **publikovat** klikněte na **Importovat profil**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   V dialogovém okně **vybrat cíl publikování** klikněte na **Importovat profil**.
   ::: moniker-end

   ![Zvolit publikování](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Přejděte do umístění souboru nastavení publikování, který jste vytvořili v předchozí části.

1. V dialogovém okně **importovat soubor nastavení publikování** přejděte na a vyberte profil, který jste vytvořili v předchozí části, a klikněte na **otevřít**.

   ::: moniker range=">=vs-2019"
   Kliknutím na tlačítko **Dokončit** uložte profil publikování a potom klikněte na tlačítko **publikovat**.

   Visual Studio spustí proces nasazení a v okně výstup se zobrazí průběh a výsledky.

   Pokud se zobrazí nějaké chyby nasazení, klikněte na **Upravit** a upravte nastavení. Upravte nastavení a kliknutím na **ověřit** otestujte nová nastavení. Pokud se název hostitele nenajde, zkuste IP adresu místo názvu hostitele v polích **Server** a **cílová adresa URL** .
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio spustí proces nasazení a v okně výstup se zobrazí průběh a výsledky.

   Pokud se zobrazí nějaké chyby nasazení, klikněte na **Nastavení** a upravte nastavení. Upravte nastavení a kliknutím na **ověřit** otestujte nová nastavení. Pokud se název hostitele nenajde, zkuste IP adresu místo názvu hostitele v polích **Server** a **cílová adresa URL** .
   ::: moniker-end

   ![Upravit nastavení v nástroji pro publikování](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
