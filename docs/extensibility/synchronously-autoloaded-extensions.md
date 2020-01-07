---
title: Automaticky synchronně načítaná rozšíření
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa26585ff4cca909a7fb7c955b351b8860436b4
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75406619"
---
# <a name="synchronously-autoloaded-extensions"></a>Automaticky synchronně načítaná rozšíření

Synchronně převedená rozšíření mají negativní vliv na výkon sady Visual Studio a měla by být převedena na použití asynchronního automatického načtení. Ve výchozím nastavení aplikace Visual Studio 2019 blokuje synchronně automaticky načtené balíčky z libovolného rozšíření a uživatele upozorní.

![Upozornění kompatibility rozšíření](media/extension-compatibility-warning-16-1.png.png)

Můžeš:

- Kliknutím na zapnout **synchronní automatické načítání** povolíte rozšíření automatické načítání. Chcete-li toto nastavení změnit v aplikaci Visual Studio, klikněte na prostředí, pak na rozšíření a potom zaškrtněte políčko "povolí synchronní automatické načtení rozšíření". 

- Kliknutím na **spravovat výkon** otevřete [dialogové okno Správce výkonu](#performance-manager-dialog) , ve kterém se zobrazí problémy s výkonem s rozšířeními a okny nástrojů.

- Pokud chcete oznámení zavřít a zabránit budoucím oznámením z existujících nainstalovaných rozšíření, klikněte na **nezobrazit tuto zprávu pro aktuální rozšíření** . Pokud přidáte nové rozšíření, které se autoloade synchronně, zobrazí se toto oznámení znovu. Budete dál dostávat oznámení o dalších funkcích sady Visual Studio.

## <a name="performance-manager-dialog"></a>Dialogové okno Správce výkonu

![Dialogové okno Správce výkonu](media/performance-manager.png)

Všechna rozšíření, která synchronně načetla jakékoli balíčky v uživatelských relacích, se zobrazí na kartě **zastaralá rozhraní API** .

* Pokud chcete získat další informace o zastaralých rozhraních API, klikněte na **Další informace o tomto problému** .
* Pro průběh migrace se obraťte na dodavatele rozšíření.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Zadání nastavení synchronního automatického načtení pomocí zásad skupiny

Správci mohou Zásady skupiny povolit synchronní automatické načítání. Uděláte to tak, nastavte zásadu založenou na registru pro následující klíč:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Entry = **povoleno**

Hodnota = (DWORD)
* **0** je synchronní automatické načítání není povolené.
* **1** je povolené synchronní automatické načítání.

## <a name="extension-authors"></a>Autoři rozšíření
Autoři rozšíření můžou najít pokyny pro migraci balíčků do asynchronního automatického načítání při [migraci na AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="see-also"></a>Viz také:
Další informace o nastavení synchronního automatického načítání v aplikaci Visual Studio 2019 naleznete na stránce [synchronní chování automatického načtení](https://aka.ms/AA52xzw) .
