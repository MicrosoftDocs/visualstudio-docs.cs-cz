---
title: Pole pro hledání | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b7c5f9c19573a04b1d9a8d7b8c6e9450aef9bc44
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645735"
---
# <a name="findcommand-box"></a>Pole Najít/příkaz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vyhledat text a spustit příkazy sady Visual Studio z pole **Najít/příkaz** . Pole **Najít/příkaz** je stále k dispozici jako ovládací prvek panelu nástrojů, ale ve výchozím nastavení se už nezobrazuje. Pole **Najít/příkaz** můžete zobrazit tak, že na panelu nástrojů **Standard** kliknete na **tlačítko Přidat nebo odebrat tlačítka** a pak zvolíte **Najít**.

 Chcete-li spustit příkaz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zaregistrujte ho pomocí znaku většího než (>).

 Pole **Najít/příkaz** zachová poslední 20 zadaných položek a zobrazí je v rozevíracím seznamu. Seznam můžete procházet výběrem kláves se šipkami.

 ![Najít&#47;– příkazové okno](../ide/media/findcommandbox.png "FindCommandBox") Pole Najít/příkaz

## <a name="searching-for-text"></a>Hledání textu
 Ve výchozím nastavení, když zadáte text do pole **Najít/příkaz** a pak zvolíte klávesu ENTER, Visual Studio prohledá aktuální dokument nebo nástroj pomocí možností, které jsou zadány v dialogovém okně **najít v souborech** . Další informace najdete v tématu [hledání a nahrazování textu](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Zadávání příkazů
 Chcete-li použít pole **Najít/příkaz** k vystavení jednoho [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ho příkazu nebo aliasu místo hledání textu, zadejte příkaz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], který je uvozen symbolem větším než (>). Příklad:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

 Alternativně můžete také použít okno Příkaz k zadání a spuštění jednoho nebo více příkazů. Některé příkazy nebo aliasy lze zadat a provádět sami; ostatní mají ve své syntaxi požadované argumenty. Seznam příkazů, které mají argumenty, naleznete v tématu [Visual Studio Commands](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Řídicí znaky
 Znak stříšky (^) na příkazovém řádku znamená, že znak bezprostředně za ním je interpretován doslova, nikoli jako řídicí znak. To lze použít k vložení přímých uvozovek ("), mezer, počátečních lomítek, znakových přepínačů nebo jiných literálových znaků v parametru nebo hodnotě přepínače s výjimkou názvů přepínačů. Například

```
>Edit.Find ^^t /regex
```

 Blikající kurzor funguje stejně, bez ohledu na to, zda se nachází uvnitř nebo vně uvozovek. Pokud je poslední znak na řádku blikající kurzor, ignoruje se.

## <a name="see-also"></a>Viz také
 [Příkazové okno](../ide/reference/command-window.md) pro [hledání a nahrazování textu](../ide/finding-and-replacing-text.md)
