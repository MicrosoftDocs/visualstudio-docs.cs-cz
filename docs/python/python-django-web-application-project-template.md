---
title: Šablona webového projektu Django pro Python
description: Visual Studio poskytuje komplexní šablonu pro rychlé vytváření webových aplikací Django s Pythonem.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 136c03ef11071e5d548e36e45a6a541cffce1469
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784840"
---
# <a name="django-web-project-template"></a>Šablona webového projektu Django

[Django](https://www.djangoproject.com/) je architektura Pythonu na vysoké úrovni určená pro rychlý, bezpečný a škálovatelný vývoj webových aplikací. Podpora Pythonu v sadě Visual Studio poskytuje několik šablon projektů pro nastavení struktury webové aplikace založené na Django. Chcete-li použít šablonu v sadě Visual Studio, vyberte **možnost Soubor** > **nový** > **projekt**, vyhledejte "Django" a vyberte z **prázdných webových projektů Django**, **webového projektu Django**a šablon **webových projektů Django.** Podívejte se na [výukový program Learn Django,](learn-django-in-visual-studio-step-01-project-and-solution.md) kde najdete návod ke všem šablonám.

Visual Studio poskytuje plnou intelliSense pro projekty Django:

- Kontextové proměnné předané do šablony:

    ![Technologie IntelliSense pro kontextové proměnné](media/template-django-intellisense.png)

- Označování a filtrování pro vestavěné i uživatelsky definované:

    ![Technologie IntelliSense pro značky a filtry](media/template-django-intellisense-filter.png)

- Syntaxe zbarvení pro vložené CSS a JavaScript:

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio také poskytuje plnou [podporu ladění](debugging-python-in-visual-studio.md) pro projekty Django:

![Zarážky](media/template-django-debugging.png)

Je typické pro django projekty, které mají být spravovány prostřednictvím jejich *manage.py* souboru, což je předpoklad, že Visual Studio následuje. Pokud tento soubor přestanete používat jako vstupní bod, v podstatě přerušíte soubor projektu. V takovém případě je třeba [znovu vytvořit projekt z existujících souborů](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) bez označení jako projekt Django.

## <a name="django-management-console"></a>Konzola pro správu Django

Konzola pro správu Django je přístupná pomocí různých příkazů v nabídce **Projekt** nebo kliknutím pravým tlačítkem myši na projekt v **Průzkumníku řešení**.

- **Otevřít Prostředí Django**: otevře prostředí v kontextu aplikace, které umožňuje manipulovat s modely:

    ![Výsledky příkazu Otevřít prostředí Django](media/template-django-console-shell.png)

- **Django Sync DB** `manage.py syncdb` : spustí se v **interaktivním** okně:

    ![Výsledek příkazu Django Sync DB](media/template-django-console-sync-db.png)

- **Sbírat statické** `manage.py collectstatic --noinput` : provede zkopírovat všechny statické `STATIC_ROOT` soubory na cestu určenou ve vašem *settings.py*.

    ![Výsledek příkazu Shromáždit statickou](media/template-django-console-collect-static.png)

- **Ověřit**: `manage.py validate`provede , který hlásí všechny chyby `INSTALLED_APPS` ověření v nainstalovaných modelech určených *v settings.py*:

    ![Výsledek příkazu Ověřit](media/template-django-console-validate.png)

## <a name="see-also"></a>Viz také

- [Naučte se Django výukový program](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
