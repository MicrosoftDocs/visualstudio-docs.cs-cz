---
title: Příkaz ShowWebBrowser – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ecf86bdc7516f05935bd944f23633b3baad2c7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663525"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zobrazuje adresu URL, kterou zadáte v okně webového prohlížeče, a to buď v rámci integrovaného vývojového prostředí (IDE), nebo mimo rozhraní IDE.

## <a name="syntax"></a>Syntaxe

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumenty
 `URL` Požadovanou. Adresa URL (Uniform Resource Locator) pro web

## <a name="switches"></a>Přepínače
 /New je nepovinný. Určuje, že se stránka zobrazí v nové instanci webového prohlížeče.

 /EXT je nepovinný. Určuje, že se stránka zobrazí ve výchozím webovém prohlížeči mimo rozhraní IDE.

## <a name="remarks"></a>Poznámky
 Alias pro příkaz **ShowWebBrowser –** je **Navigate** nebo **NAV**.

## <a name="example"></a>Příklad
 Následující příklad zobrazuje domovskou stránku MSDN online ve webovém prohlížeči mimo rozhraní IDE. Pokud je již otevřena instance webového prohlížeče, je použita. v opačném případě se spustí nová instance.

```
>View.ShowWebBrowser https://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
