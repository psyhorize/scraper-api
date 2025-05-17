from fastapi import FastAPI, Request
from pydantic import BaseModel
from typing import Optional
import uvicorn

# Przykladowy scraper placeholder (na razie zwraca testowe dane)
def analyze_item(description: str, image_url: Optional[str] = None):
    # Tu docelowo podlaczymy scrapery Vinted, eBay itd.
    return {
        "typ": "Buty sportowe",
        "marka": "Nike",
        "rynek_niemcy": {
            "nowa_cena": "129.99 EUR",
            "uzywana_min": "49.99 EUR",
            "uzywana_max": "89.99 EUR",
            "uzywana_avg": "67.45 EUR",
            "proponowana_cena": "74.99 EUR"
        },
        "rynek_francja": "średnia cena 69 EUR",
        "rynek_polska": "średnia cena 299 PLN"
    }

# Dane wejściowe z Make.com
class ItemRequest(BaseModel):
    description: str
    image_url: Optional[str] = None

# Tworzymy API
app = FastAPI()

@app.post("/scrape")
async def scrape_item(item: ItemRequest):
    result = analyze_item(description=item.description, image_url=item.image_url)
    return result

# Lokalne uruchomienie (do testu lokalnie, NIE na Railway)
# if __name__ == "__main__":
#     uvicorn.run("main:app", host="0.0.0.0", port=8000, reload=True)
