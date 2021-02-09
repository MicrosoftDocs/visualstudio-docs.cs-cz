---
title: Šablona webového projektu Django pro Python
description: Visual Studio poskytuje komplexní šablonu pro rychlé vytváření Django webových aplikací pomocí Pythonu.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 0193256edb4a55285e8017a56fe7249ef5d60362
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912402"
---
# <a name="django-web-project-template"></a>Šablona webového projektu Django

[Django](https://www.djangoproject.com/) je špičková architektura Pythonu navržená pro rychlý, zabezpečený a škálovatelný webový vývoj. Podpora Pythonu v sadě Visual Studio poskytuje několik šablon projektů pro nastavení struktury webové aplikace založené na Django. Chcete-li použít šablonu v aplikaci Visual Studio, vyberte **soubor**  >  **Nový**  >  **projekt**, vyhledejte "Django" a vyberte možnost z **prázdného webového projektu Django**, **Django webového projektu** a **hlasování Django šablony webového projektu** . Návod pro všechny šablony najdete v [kurzu učení Django](learn-django-in-visual-studio-step-01-project-and-solution.md) .

Visual Studio poskytuje kompletní technologii IntelliSense pro projekty Django:

- Kontextové proměnné předané do šablony:

    ![IntelliSense pro kontextové proměnné](media/template-django-intellisense.png)

- Označování a filtrování pro předdefinované i definované uživatelem:

    ![IntelliSense pro značky a filtry](media/template-django-intellisense-filter.png)

- Barevné zvýrazňování syntaxe pro vložené šablony stylů CSS a JavaScript:

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio také poskytuje úplnou [podporu ladění](debugging-python-in-visual-studio.md) pro projekty Django:

![Zarážky](media/template-django-debugging.png)

Je typický pro Django projekty, které se mají spravovat prostřednictvím jejich souboru *Manage.py* , což je předpokladem, že následuje aplikace Visual Studio. Pokud tento soubor zastavíte jako vstupní bod, v podstatě je nutné soubor projektu rozdělit. V takovém případě je nutné [znovu vytvořit projekt z existujících souborů](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) bez označení jako projekt Django.

## <a name="django-management-console"></a>Konzola pro správu Django

Konzola pro správu Django je k dispozici prostřednictvím různých příkazů v nabídce **projekt** nebo kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení**.

- **Otevřít prostředí Django**: otevře prostředí v kontextu vaší aplikace, které vám umožní manipulovat s vašimi modely:

    ![Výsledky příkazu otevřít prostředí Django](media/template-django-console-shell.png)

- **Django Sync DB**: provede `manage.py syncdb` se v **interaktivním** okně:

    ![Výsledek příkazu Django Sync DB](media/template-django-console-sync-db.png)

- **Collect static**: provede `manage.py collectstatic --noinput` kopírování všech statických souborů do cesty určené `STATIC_ROOT` v *Settings.py*.

    ![Výsledek příkazu Collect static](media/template-django-console-collect-static.png)

- **Validate**: spuštěno `manage.py validate` , které hlásí všechny chyby ověřování v instalovaných modelech určených `INSTALLED_APPS` ve vašem *Settings.py*:

    ![Výsledek příkazu Validate](media/template-django-console-validate.png)

## <a name="see-also"></a>Viz také

- [Kurz k seznámení s Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
