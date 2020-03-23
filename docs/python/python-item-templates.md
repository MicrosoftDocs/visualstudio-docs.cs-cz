---
title: Šablony položek pro projekty Pythonu
description: Referenční seznam šablon položek pro projekt Pythonu, které jsou k dispozici prostřednictvím dialogového okna Přidat > novou položku v sadě Visual Studio.
ms.date: 12/06/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c093dad1364fd5209f51c8e87e3fb99b3c1d3c4a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430335"
---
# <a name="python-item-templates"></a>Šablony položek Pythonu

Šablony položek jsou dostupné v projektech Pythonu pomocí **příkazu příkazu** > Nabídka**Přidat novou položku** projektu nebo **příkazu Přidat** > **novou položku** v místní nabídce v **Průzkumníku řešení**.

![Dialogové okno Přidat novou položku](media/project-item-templates.png)

Pomocí názvu, který pro položku zadáte, šablona obvykle vytvoří jeden nebo více souborů a složek v rámci aktuálně vybrané složky v projektu (klepnutím pravým tlačítkem myši na složku automaticky vybere tuto složku). Přidání položky ji zahrnuje v projektu sady Visual Studio a zobrazí se v **Průzkumníku řešení**.

Následující tabulka stručně vysvětluje účinek každé šablony položky v rámci projektu Pythonu:

| Šablona | Co šablona vytváří |
| --- | --- |
| **Prázdný soubor pythonu** | Prázdný soubor s příponou *Py.* |
| **Třída Pythonu** | Soubor *.py* obsahující jednu prázdnou definici třídy Pythonu. |
| **Balíček Pythonu** | Složka obsahující * \_ \_soubor init\_\_.py.* |
| **Test jednotky Pythonu** | Soubor *PY* s jedním testováním částí `unittest` na základě rozhraní `unittest.main()` spolu s voláním ke spuštění testů v souboru. |
| **Stránka HTML** | Soubor *HTML* s jednoduchou strukturou stránky `<head>` `<body>` skládající se z prvku a. |
| **Javascript** | Prázdný soubor *JS.* |
| **Stylů** | Soubor *CSS* obsahující prázdný styl `body`pro aplikaci . |
| **Textový soubor** | Prázdný soubor *TXT.* |
| **Aplikace Django 1.9**<br/>**Aplikace Django 1.4** | Složka s názvem aplikace, která obsahuje základní soubory pro aplikaci Django, jak je vysvětleno v [Learn Django v sadě Visual Studio, Krok 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) pro Django 1.9. Pro Django 1.4 nejsou zahrnuty složky *migrace,* *soubor admin.py* a soubor *apps.py.* |
| **Ironpython WPF okno** | Okno WPF skládající se ze dvou souborů vedle sebe: *souboru .xaml,* `<Window>` který definuje a s prázdným `<Grid>` prvkem, a přidruženého souboru Py, který načte soubor XAML pomocí *.py* `wpf` knihovny. Obvykle se používá v rámci projektu vytvořeného pomocí jedné ze šablon projektu IronPython. Viz [Správa projektů Pythonu – šablony projektů](managing-python-projects-in-visual-studio.md#project-templates). |
| **Soubory podpory webových rolí** | Složka *přihrádky* v kořenovém adresáři projektu (bez ohledu na vybranou složku v projektu). Složka obsahuje výchozí skript nasazení a soubor *web.config* pro webové role Azure Cloud Service. Šablona obsahuje také soubor *readme.html,* který vysvětluje podrobnosti. |
| **Soubory podpory rolí pracovního procesu** | Složka *přihrádky* v kořenovém adresáři projektu (bez ohledu na vybranou složku v projektu). Složka obsahuje výchozí nasazení a spuštění skriptu, spolu se souborem *web.config,* pro role pracovních pracovníků Azure Cloud Service. Šablona obsahuje také soubor *readme.html,* který vysvětluje podrobnosti. |
| **Azure web.config (FastCGI)** | Soubor *web.config,* který obsahuje položky pro aplikace používající objekt [WSGI](https://wsgi.readthedocs.io/en/latest/) ke zpracování příchozích připojení. Tento soubor je obvykle nasazen do kořenového adresáře webového serveru se službou IIS. Další informace naleznete [v tématu Konfigurace aplikace pro službu IIS](configure-web-apps-for-iis-windows.md). |
| **Azure web.config (HttpPlatformHandler)** | Soubor *web.config,* který obsahuje položky pro aplikace, které poslouchají na soketu pro příchozí připojení. Tento soubor se obvykle nasadí do kořenového adresáře webového serveru se službou IIS, jako je například služba Azure App Service. Další informace naleznete [v tématu Konfigurace aplikace pro službu IIS](configure-web-apps-for-iis-windows.md). |
| **Azure statické soubory web.config** | Soubor *web.config* obvykle přidán do *statické* složky (nebo jiné složky obsahující statické položky) zakázat zpracování Pythonu pro tuto složku. Tento konfigurační soubor pracuje ve spojení s jedním z config souborů FastCGI nebo HttpPlatformHandler výše. Další informace naleznete [v tématu Konfigurace aplikace pro službu IIS](configure-web-apps-for-iis-windows.md). |
| **Azure Vzdálené ladění web.config** | Zastaralé (používá se pro vzdálené ladění ve službě Azure App Service pro Windows, která už není podporovaná). |

## <a name="see-also"></a>Viz také

- [Správa projektů Pythonu – šablony projektů](managing-python-projects-in-visual-studio.md#project-templates)
- [Šablony webových projektů pythonu](python-web-application-project-templates.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
