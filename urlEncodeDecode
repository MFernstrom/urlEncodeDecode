unit urlEncodeDecode;

{
  URL Encoder/Decoder based on Rosetta Code challenge for encoding/decoding
  https://rosettacode.org/wiki/URL_decoding
  https://rosettacode.org/wiki/URL_encoding

  Author  - Marcus Fernstrom
  License - Apache 2.0
  Version - 0.1
}

{$mode objfpc}{$H+}

interface

uses
  Classes, SysUtils, Dialogs, strutils;

function urlDecode(data: String):AnsiString;
function urlEncode(data: string):AnsiString;

implementation


function urlDecode(data: String): AnsiString;
var
  ch: Char;
  pos, skip: Integer;

begin
  pos := 0;
  skip := 0;
  Result := '';

  for ch in data do begin
    if skip = 0 then begin
      if (ch = '%') and (pos < data.length -2) then begin
        skip := 2;
        Result := Result + AnsiChar(Hex2Dec('$' + data[pos+2] + data[pos+3]));

      end else begin
        Result := Result + ch;
      end;

    end else begin
      skip := skip - 1;
    end;
    pos := pos +1;
  end;
end;


function urlEncode(data: string): AnsiString;
var
  ch: AnsiChar;
begin
  Result := '';
  for ch in data do begin
    if ((Ord(ch) < 65) or (Ord(ch) > 90)) and ((Ord(ch) < 97) or (Ord(ch) > 122)) then begin
      Result := Result + '%' + IntToHex(Ord(ch), 2);
    end else
      Result := Result + ch;
  end;
end;

end.
