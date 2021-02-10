---
title: ShowWebBrowser – příkaz
description: Přečtěte si o příkazu zobrazit webový prohlížeč a o tom, jak se zobrazuje adresa URL, kterou zadáte v okně webového prohlížeče v rámci integrovaného vývojového prostředí (IDE) nebo extern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9117360d795a8027812b2534311a846d0ee56e09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957605"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser – příkaz

Zobrazuje adresu URL, kterou zadáte v okně webového prohlížeče, a to buď v rámci integrovaného vývojového prostředí (IDE), nebo mimo rozhraní IDE.

## <a name="syntax"></a>Syntaxe

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
`URL`

Povinná hodnota. Adresa URL (Uniform Resource Locator) pro web

## <a name="switches"></a>přepínače,
/new

Nepovinný parametr. Určuje, že se stránka zobrazí v nové instanci webového prohlížeče.

/ext

Nepovinný parametr. Určuje, že se stránka zobrazí ve výchozím webovém prohlížeči mimo rozhraní IDE.

## <a name="remarks"></a>Poznámky
Alias pro příkaz **ShowWebBrowser –** je **Navigate** nebo **NAV**.

## <a name="example"></a>Příklad
Následující příklad zobrazuje domovskou stránku Microsoft Docs ve webovém prohlížeči mimo rozhraní IDE. Pokud je již otevřena instance webového prohlížeče, je použita. v opačném případě se spustí nová instance.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)