```csharp
using System.Collections.Generic;

namespace PersonaGrata
{
    public class Location
    {
        public List<Coordinate> Coordinates { get; set; }

        public override string ToString()
        {
            string result = string.Empty;

            if (Coordinates.Count > 0)
            {
                result += $"    Coordinates:\n";

                foreach (var item in Coordinates)
                {
                    result += $"{item}";
                }
            }

            return result;
        }

    }
}
```
