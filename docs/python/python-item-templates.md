---
title: Šablony položek pro projekty v Pythonu
description: Seznam odkazů šablon položek pro projekt Pythonu, které jsou k dispozici v dialogovém okně Přidat > novou položku v aplikaci Visual Studio.
ms.date: 12/06/2018
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 528606356c2d976de71ab2c0317a1a0236d2e63f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533390"
---
# <a name="python-item-templates"></a>Šablony položek Pythonu

Šablony položek jsou k dispozici v projektech Pythonu **Project**pomocí  >  příkazu nabídky projekt**Přidat novou položku** nebo příkazu **Přidat**  >  **novou položku** v kontextové nabídce v **Průzkumník řešení**.

![Dialogové okno Přidat novou položku](media/project-item-templates.png)

Pomocí názvu, který zadáte pro položku, šablona obvykle vytvoří jeden nebo více souborů a složek v rámci aktuálně vybrané složky v projektu (kliknutím pravým tlačítkem myši na složku zobrazíte místní nabídku, která tuto složku automaticky vybere). Přidání položky zahrne do projektu aplikace Visual Studio a položka se zobrazí v **Průzkumník řešení**.

Následující tabulka stručně vysvětluje účinek každé šablony položky v rámci projektu Python:

| Šablona | Jak šablona vytvoří |
| --- | --- |
| **Prázdný soubor Pythonu** | Prázdný soubor s příponou *. py* . |
| **Python – třída** | Soubor *. py* obsahující jednu prázdnou definici třídy Pythonu. |
| **Balíček Pythonu** | Složka, která obsahuje soubor * \_ \_ init \_ \_ . py* . |
| **Test jednotek Pythonu** | Soubor *. py* s jednou jednotkou testu založenou na `unittest` rozhraní, spolu s voláním pro `unittest.main()` spuštění testů v souboru. |
| **Stránka HTML** | Soubor *. html* s jednoduchou strukturou stránky skládající se z `<head>` prvku a `<body>` . |
| **JavaScript** | Prázdný soubor *. js* . |
| **Šablona stylů** | Soubor *. CSS* obsahující prázdný styl pro `body` . |
| **Textový soubor** | Prázdný soubor *. txt* . |
| **Aplikace Django 1,9**<br/>**Aplikace Django 1,4** | Složka s názvem aplikace, která obsahuje základní soubory pro aplikaci Django, jak je vysvětleno v tématu [informace Django v aplikaci Visual Studio, krok 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) pro Django 1,9. Pro Django 1,4 nejsou zahrnuty složky *migrace* , soubor *admin.py* a soubor *Apps.py* . |
| **Ironpythonu okno WPF** | Okno WPF sestávající ze dvou souběžných souborů: soubor *. XAML* , který definuje `<Window>` s prázdným `<Grid>` elementem, a přidružený soubor *. py* , který načte soubor XAML pomocí `wpf` knihovny. Obvykle se používá v rámci projektu vytvořeného pomocí jedné z šablon projektů Ironpythonu. Viz [Správa projektů Pythonu – šablony projektů](managing-python-projects-in-visual-studio.md#project-templates). |
| **Soubory podpory webové role** | Složka *bin* v kořenovém adresáři projektu (bez ohledu na vybranou složku v projektu). Složka obsahuje výchozí skript nasazení a soubor *web.config* pro webové role cloudové služby Azure. Šablona také obsahuje soubor *readme.html* , který vysvětluje podrobnosti. |
| **Podpůrné soubory role pracovního procesu** | Složka *bin* v kořenovém adresáři projektu (bez ohledu na vybranou složku v projektu). Složka obsahuje výchozí nasazení a spouštěcí skript spolu s *web.config* souborem pro role pracovních procesů cloudové služby Azure. Šablona také obsahuje soubor *readme.html* , který vysvětluje podrobnosti. |
| **Rozhraní Azure web.config (FastCGI)** | *web.config* soubor, který obsahuje položky pro aplikace, které používají objekt [rozhraním WSGI](https://wsgi.readthedocs.io/en/latest/) ke zpracování příchozích připojení. Tento soubor je obvykle nasazen do kořenového adresáře webového serveru, na kterém je spuštěna služba IIS. Další informace najdete v tématu [Konfigurace aplikace pro službu IIS](configure-web-apps-for-iis-windows.md). |
| **web.config Azure (HttpPlatformHandler)** | *web.config* soubor, který obsahuje položky pro aplikace, které naslouchají na soketu pro příchozí připojení. Tento soubor je obvykle nasazen do kořenového adresáře webového serveru, na kterém je spuštěna služba IIS, například Azure App Service. Další informace najdete v tématu [Konfigurace aplikace pro službu IIS](configure-web-apps-for-iis-windows.md). |
| **web.configstatických souborů Azure** | Soubor *web.config* obvykle přidaný do *statické* složky (nebo jiné složky obsahující statické položky) pro zakázání manipulace s Pythonem pro tuto složku. Tento konfigurační soubor funguje ve spojení s jedním ze souborů konfigurace FastCGI nebo HttpPlatformHandler výše. Další informace najdete v tématu [Konfigurace aplikace pro službu IIS](configure-web-apps-for-iis-windows.md). |
| **Vzdálené ladění Azure web.config** | Zastaralé (bylo použito pro vzdálené ladění v Azure App Service pro Windows, které již není podporováno). |

## <a name="see-also"></a>Viz také:

- [Správa projektů Pythonu – šablony projektů](managing-python-projects-in-visual-studio.md#project-templates)
- [Šablony webových projektů v Pythonu](python-web-application-project-templates.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
