var fso = new ActiveXObject("Scripting.FileSystemObject");
var f = fso.OpenTextFile(WScript.Arguments(0));
var text = "";
while (!f.AtEndOfStream)
    text += f.ReadLine();
f.Close();
WSH.echo("Write needed substring");
t = WScript.StdIn.ReadLine()
//t='abaxabaz'
m = t.length
alph = new Array()
//Определяем алфавит строки t
for (i = 0; i < m; i++)
    alph[t.charAt(i)] = 0
//В двумерном массиве del будем хранить таблицу переходов
del = new Array(m + 1)
for (j = 0; j <= m; j++)
    del[j] = new Array()
//Инициализируем таблицу переходов
for (i in alph)
    del[0][i] = 0
//Формируем таблицу переходов
for (j = 0; j < m; j++) {
    prev = del[j][t.charAt(j)]
    del[j][t.charAt(j)] = j + 1
    for (i in alph)
        del[j + 1][i] = del[prev][i]
}
/*Выводим таблицу переходов
for (j = 0; j <= m; j++) {
    out = ''
    for (i in alph)
        out += del[j][i] + ' '
    WScript.Echo(out)
}*/
var state = 0;
var start = new Date;
for (j = 0; j < 10; j++) {
    var indexesOfEntering = new Array();

    for (var i = 0; i <= text.length; i++) {
        if (del[state][text.charAt(i)])
            state = del[state][text.charAt(i)];
        else state = 0;
        if (state == t.length) {
            indexesOfEntering.push(i - t.length + 1);
        }
    }
}
var end = new Date;
var time = (end - start) / 10;
WSH.echo("average time:", time);
WSH.echo(indexesOfEntering.join(","));
WSH.echo(indexesOfEntering.length);
