---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 175cb6f6a8a3f240c244e139406841b0546209cc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295906"
---
# <a name="javascript-in-visual-studio"></a>JavaScript ve Visual Studiu 2012
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript je prvotřídní jazyk v sadě Visual Studio. Při psaní kódu v jazyce JavaScript v sadě Visual Studio IDE můžete použít téměř všechny standardní editační pomůcky (fragmenty kódu, funkci IntelliSense atd.). Můžete napsat kód jazyka JavaScript pro mnoho typů aplikací a služeb.

 Referenční dokumentaci jazyka JavaScript naleznete v tématu [JavaScript](https://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Konkrétní verze sady Visual Studio, nebo konkrétní rozšíření sady Visual Studio, může být nutné vyvíjet typy konkrétní aplikace a služby pomocí HTML a JavaScriptu. Následující seznam obsahuje odkazy na další informace.

- Pokud chcete vytvářet aplikace pro různé platformy pomocí Apache Cordova, [získejte Visual Studio Tools pro Apache Cordova](https://go.microsoft.com/fwlink/p/?LinkId=397606).

- Pokud chcete vytvořit [Windows Store](https://developer.microsoft.com/), [Windows Phone](https://developer.microsoft.com/)a univerzální aplikace (podporující obě platformy), [Získejte nástroje](https://developer.microsoft.com/windows/downloads).

- Chcete-li vytvořit cloudové služby, přečtěte si [web Microsoft Azure](https://azure.microsoft.com/documentation/).

- Informace o vytváření webů a webových aplikací [najdete na webu ASP.NET](https://dotnet.microsoft.com/apps/aspnet/web-apps).

  > [!NOTE]
  > Můžete vytvořit prázdný web ASP.Net a použít pro programování HTML, CSS a JavaScriptu. Soubor Webconfig poskytovaných technologií ASP.NET povolí ladění v sadě Visual Studio (nebo můžete použít nástroje F12 při spuštění aplikace).

  Editor jazyka JavaScript v aplikaci Visual Studio poskytuje podporu technologie IntelliSense. Další informace naleznete v tématu [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Co je nového v jazyce JavaScript
 Nové funkce pro JavaScript jsou uvedeny v následující tabulce.

|Funkce|Popis|
|-------------|-----------------|
|Třídy|Nová syntaxe podporuje deklaraci [tříd](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Co|[Příslibů](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) umožňuje snadnější a čisticí asynchronní kódování. Jsou podporovány konstruktory Promise společně s metodami `all` a `race` Utility.|
|Iterátory|Nyní můžete iterovat iterable objekty (včetně polí, jako pole objektů a iterátory), vyvolání hook vlastní iterace pomocí příkazů ke spuštění pro hodnotu každé různé vlastnosti. Další informace najdete v tématu [iterátory a generátory](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Poznámka:**  Generátory ještě nejsou podporované.|
|Funkce šipky|Funkce šipky (= >) poskytuje zkrácený Syntax pro klíčové slovo `function`, které obsahuje lexikální vazbu `this`.|
|Nové metody pro předdefinované objekty|Objekty [pole](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [objekt Math Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [číslo objektu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [objekt objektu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)a objekty [řetězce](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) v předdefinovaných objektech obsahují mnoho nových funkcí nástrojů a vlastnosti pro manipulaci a kontrolu dat.|
|Vylepšení literálu objektu|Objektů teď podporují vypočítané vlastnosti, definice stručné metod a syntaxi ve zkráceném tvaru pro vlastnosti, jehož hodnota je inicializována na proměnnou se stejným názvem. Další informace najdete v tématu [vytváření objektů](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Proxy servery|[Proxy](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) umožňují vlastní chování objektů.|
|Parametry REST|Zbývající parametry umožňují zapnout po sobě jdoucí argumenty ve volání funkce na pole. Další informace najdete v tématu [funkce](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Spread – operátor|[Operátor rozprostření](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) rozbalí výrazy iterující do jednotlivých argumentů. Například `a.b(…array)` je přibližně stejný jako `a.b.apply(a, array)`.|
|Symboly|Objekty [symbolů](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) umožňují přidání vlastností do existujících objektů bez možnosti rušivého narušování s existujícími vlastnostmi objektu bez nezamýšlené viditelnosti a bez dalších nekoordinujících dodatků jiným kódem.|
|Řetězce šablon|[Řetězce šablon](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) jsou řetězcové literály, které umožňují vyhodnotit výrazy a zřetězit je pomocí řetězcového literálu.|
|Vylepšení kódování Unicode|Vylepšili jsme podporu kódování Unicode. Nový formát sekvence escape například podporuje astral kódových bodů (body kódu obsahující více než čtyři šestnáctkové číslice). Další informace najdete v tématu [speciální znaky](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|[Weakset](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) je kolekce objektů, které budou uvolněny z paměti, pokud neodkazují kamkoli jinde.|
