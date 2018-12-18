---
title: Šablony položek pro projekty v Pythonu
description: Referenční seznam šablon položek pro projekt v Pythonu, které jsou k dispozici prostřednictvím Přidat > Nová položka dialogového okna v sadě Visual Studio.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5fc08a190dfe146002dc4180f8c9a1fb680a5fb9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065785"
---
# <a name="python-item-templates"></a>Šablony položek Pythonu

Jsou k dispozici v projektů v Pythonu pomocí šablony položky **projektu** > **přidat novou položku** příkaz nabídky nebo **přidat**  >  **Nová položka** příkazu v místní nabídce v **Průzkumníka řešení**.

![Přidat novou položku – dialogové okno](media/project-item-templates.png)

Pomocí názvu, který zadáte pro položku, šablony obvykle vytvoří jednu nebo více soubory a složky v rámci vybrané složky v projektu (pravým tlačítkem myši na složku, do které vyvolali místní nabídku automaticky vybere tuto složku). Přidání položky obsahuje v projektu sady Visual Studio a se položka zobrazí v **Průzkumníka řešení**.

Následující tabulka stručně popisuje efekt každé šablony položky v rámci projektu Pythonu:

| Šablony | Šablona vytvoří |
| --- | --- |
| **Prázdný soubor Pythonu** | Prázdný soubor s *.py* rozšíření. |
| **Třída Pythonu** | A *.py* soubor, který obsahuje jednu definici prázdná třída Pythonu. |
| **Balíček Pythonu** | Složka, která obsahuje  *\_ \_init\_\_.py* souboru. |
| **Test jednotky Pythonu** | A *.py* na základě souboru s testem jedna jednotka `unittest` rozhraní .NET framework, spolu s volání `unittest.main()` ke spuštění testů v souboru. |
| **Stránka HTML** | *.Html* soubor se strukturou jednoduché stránky skládající se z `<head>` a `<body>` elementu. |
| **JavaScript** | Prázdná *js* souboru. |
| **Šablona stylů** | A *.css* soubor, který obsahuje prázdný styl `body`. |
| **Textový soubor** | Prázdná *.txt* souboru. |
| **Aplikace Django 1.9**<br/>**Aplikace Django 1.4** | Složka s názvem aplikaci, která obsahuje soubory jádra pro aplikaci Django, jak je popsáno v [další Django v sadě Visual Studio, krok 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) pro Django 1.9. Pro Django 1.4 *migrace* složku, *admin.py* souboru a *apps.py* souboru nejsou zahrnuty. |
| **Okno WPF v Ironpythonu** | Okno WPF obsahuje dva soubory vedle sebe: *.xaml* soubor, který definuje `<Window>` s prázdnou `<Grid>` elementu a přidružené *.py* soubor, který načte soubor XAML pomocí `wpf` knihovny. Obvykle se používá v rámci projektu vytvořeného pomocí jedné z šablon projektu Ironpythonu. Zobrazit [projektů v Pythonu spravovat – šablony projektů](managing-python-projects-in-visual-studio.md#project-templates). |
| **Soubory podpory webové Role** | A *bin* složky v kořenové složce projektu (bez ohledu na vybrané složky v projektu). Složka obsahuje výchozí skript nasazení a *web.config* soubor pro webové role Azure Cloud Service. Také obsahuje šablony *readme.html* soubor, který vysvětluje podrobnosti. |
| **Podpůrné soubory pro Role pracovního procesu** | A *bin* složky v kořenové složce projektu (bez ohledu na vybrané složky v projektu). Složka obsahuje výchozí skript nasazení a spuštění, spolu s *web.config* soubor rolí pracovních procesů cloudových služeb Azure. Také obsahuje šablony *readme.html* soubor, který vysvětluje podrobnosti. |
| **Web.config pro Azure (FastCGI)** | A *web.config* soubor, který obsahuje položky pro aplikace s využitím [s rozhraním WSGI](https://wsgi.readthedocs.io/en/latest/) objekt pro zpracování příchozích připojení. Tento soubor je obvykle nasazeni do kořenového adresáře webový server se službou IIS. Další informace najdete v tématu [konfigurace aplikace pro službu IIS](configure-web-apps-for-iis-windows.md). |
| **Web.config pro Azure (HttpPlatformHandler)** | A *web.config* soubor, který obsahuje položky pro aplikace, které naslouchat na soket pro příchozí připojení. Tento soubor je obvykle nasazeni do kořenového adresáře webový server se službou IIS, jako je Azure App Service. Další informace najdete v tématu [konfigurace aplikace pro službu IIS](configure-web-apps-for-iis-windows.md). |
| **Web.config pro statické soubory Azure** | A *web.config* obvykle přidá do souboru *statické* složky (nebo jiné složky položky obsahující statickou) zakáže zpracování Pythonu pro tuto složku. Tento konfigurační soubor funguje ve spojení s jednou z FastCGI nebo HttpPlatformHandler konfigurační soubory výše. Další informace najdete v tématu [konfigurace aplikace pro službu IIS](configure-web-apps-for-iis-windows.md). |
| **Web.config pro Azure vzdáleného ladění** | Zastaralé (byl použit pro vzdálené ladění ve službě Azure App Service pro Windows, které již nejsou podporovány). |

## <a name="see-also"></a>Viz také:

- [Správa projektů v Pythonu – šablony projektů](managing-python-projects-in-visual-studio.md#project-templates)
- [Šablony webových projektů Python](python-web-application-project-templates.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
