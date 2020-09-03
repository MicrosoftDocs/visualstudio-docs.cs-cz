---
ms.openlocfilehash: f286002112667ba763419f0e3d6265dbe1942212
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173869"
---

1. V počítači, kde máte otevřený projekt ASP.NET v aplikaci Visual Studio, klikněte pravým tlačítkem na projekt v Průzkumník řešení a vyberte **publikovat**.

1. Pokud jste již dříve nakonfigurovali všechny publikační profily, otevře se podokno **publikování** . Klikněte na **vytvořit nový profil**.

1. V dialogovém okně **vybrat cíl publikování** klikněte na **Importovat profil**.

    ![Zvolit publikování](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Přejděte do umístění souboru nastavení publikování, který jste vytvořili v předchozí části.

1. V dialogovém okně **importovat soubor nastavení publikování** přejděte na a vyberte profil, který jste vytvořili v předchozí části, a klikněte na **otevřít**.

    Visual Studio spustí proces nasazení a v okně výstup se zobrazí průběh a výsledky.

    Pokud se zobrazí nějaké chyby nasazení, klikněte na **Nastavení** a upravte nastavení. Upravte nastavení a kliknutím na **ověřit** otestujte nová nastavení. Pokud se název hostitele nenajde, zkuste IP adresu místo názvu hostitele v polích **Server** a **cílová adresa URL** .

    ![Upravit nastavení v nástroji pro publikování](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
